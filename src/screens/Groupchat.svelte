<!--
	Home but it's a group chat.
-->
<script>
	import {
		chatName,
		chatMembers,
		chatid,
		modalShown,
		modalPage,
		profileClicked_GC,
	} from "../lib/stores.js";
	import {mobile} from "../lib/responsiveness.js";
	import Member from "../lib/Member.svelte";
	import Container from "../lib/Container.svelte";
	import * as clm from "../lib/clmanager.js";
	import PostList from "../lib/PostList.svelte";

	let showMembers = !$mobile;
</script>

<!--
	so {cmd: direct, val: {cmd: add_to_chat, val: {chatid: "", username: ""}}}?
	also  remove_from_chat
-->

<div class="groupchat">
	{#await loadPage(1)}
		<div class="fullcenter">
			<Loading />
		</div>
	{:then}
		<div id="chat">
			<Container>
				<h1>{$chatName}</h1>
				Admin ID: {$chatid}
				{#if $chatid !== "livechat"}
					<div class="settings-controls">
						<button
							class="circle members"
							on:click={() => {
								showMembers = !showMembers;
							}}
						/>
					</div>
				{/if}
			</Container>
			{#if $user.name}
				<form
					class="createpost"
					autocomplete="off"
					on:submit|preventDefault={e => {
						postErrors = "";
						if (!e.target[0].value.trim()) {
							postErrors = "You can't send blank messages!";
							return false;
						}

						spinner.set(true);

						e.target[1].disabled = true;
						link.send({
							cmd: "direct",
							val: {
								cmd: "post_chat",
								val: {
									p: e.target[0].value,
									chatid: $chatid,
								},
							},
							listener: "post_chat",
						});
						const postListener = link.on("statuscode", cmd => {
							if (cmd.listener !== "post_chat") return;
							link.off(postListener);
							spinner.set(false);

							e.target[1].disabled = false;

							if (cmd.val === "I:100 | OK") {
								e.target[0].value = "";
								e.target[0].rows = "1";
								e.target[0].style.height = "45px";
							} else if (
								cmd.val === "E:106 | Too many requests"
							) {
								postErrors = "You write very fast!";
							} else {
								postErrors =
									"Unexpected " + cmd.val + " error!";
							}
						});
						return false;
					}}
				>
					<textarea
						type="text"
						class="white"
						placeholder="Writing something..."
						id="postinput"
						name="postinput"
						autocomplete="false"
						maxlength="360"
						rows="1"
						use:autoresize
						on:input={() => {
							if ($lastTyped + 1500 < +new Date()) {
								lastTyped.set(+new Date());
								link.send({
									cmd: "direct",
									val: {
										cmd: "set_chat_state",
										val: {
											chatid: $chatid,
											state: 100,
										},
									},
									listener: "typing_indicator",
								});
							}
						}}
						on:keydown={event => {
							if (event.key == "Enter" && !shiftHeld) {
								event.preventDefault();
								document.getElementById("submitpost").click();
							}
						}}
					/>
					<button id="submitpost">SNOW FEET</button>
				</form>
				<div class="post-errors">{postErrors}</div>
			{/if}
			<TypingIndicator />
			{#if posts.length < 1}
				{#if $user.name}
					There is no entry here. Come back later or write first!
				{:else}
					How did you get into a group chat without being signed in?
				{/if}
			{:else}
				{#each posts as post (post.id)}
					<div
						transition:fly|local={{y: -50, duration: 250}}
						animate:flip={{duration: 250}}
					>
						<Member member={chatmember} />
					</button>
				{/each}

				<div class="center">
					{#if pageLoading}
						<Loading />
					{:else if numPages && numPages > pagesLoaded}
						<button
							class="load-more"
							on:click={() => loadPage(pagesLoaded + 1)}
						>
							Download again
						</button>
					{/if}
				</div>
			</div>
		{/if}
	{:catch error}
		<Container>
			<h1>{chatName}</h1>
			This message could not be sent. try again
			<pre><code>{error}</code></pre>
		</Container>
	{/await}
</div>

<style>
	.member-button {
		padding: 0;
		margin: 0;

		width: 100%;

		background-color: transparent;
		color: var(--foreground);
		border: none;

		position: relative;
		text-align: left;
	}

	/* repetition because of CSS specificity */
	:global(main.input-hover) .member-button.member-button:hover,
	.member-button.member-button:focus-visible {
		background-color: #7773;
	}
	:global(#main) .member-button.member-button:active {
		background-color: #7776;
	}
	:global(#main.layout-mobile) #chat:not(.active) {
		display: none;
	}

	.groupchat {
		display: flex;
		flex-wrap: nowrap;
		flex-direction: row;
		gap: 0.4em;
	}
	#chat {
		flex-shrink: 1;
		flex-grow: 1;
		overflow: hidden;
	}
	#members {
		height: var(--view-height);
		width: min(45%, 12em);

		background-color: var(--background);
		border: solid 2px var(--orange);
		border-radius: 1px;
		box-sizing: border-box;

		position: sticky;
		top: 0;

		flex-shrink: 0;
		flex-grow: 0;
	}
	:global(#main.layout-mobile) #members {
		width: 100%;
	}
	#members-inner {
		position: relative;

		overflow-y: auto;
		overflow-x: hidden;
		overscroll-behavior: none;

		height: calc(100% - 2.25em);
		margin-top: 2.25em;
	}

	.top {
		position: absolute;
		top: 0;
		width: 100%;
	}

	.chat-name {
		margin: 0;
	}
	.chat-id {
		font-weight: normal;
		color: #7f7f7f;
		font-size: 1rem;
	}

	.settings-controls {
		position: absolute;
		top: 0.25em;
		right: 0.25em;
	}
	.members-title {
		margin: 0.25em;
	}

	.small {
		font-size: 75%;
	}
</style>
