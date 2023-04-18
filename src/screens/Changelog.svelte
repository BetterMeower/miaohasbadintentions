<script>
	import Container from "../lib/Container.svelte";
</script>

<Container>
	<h1>check the disk</h1>
	E
</Container>
<Container>
	<h2>1.6</h2>
	<ul>
		<li>If you change your password now, we won't be able to access all your devices</li>
		<li>Refreshed the ribbon</li>
		<li>Add https://forums.meower.org/ and https://nextcloud.meower.org/ to the list of approved video providers.</li>
	</ul>
</Container>
<Container>
	<h2>1.5.2</h2>
	<ul>
		<li>Bad pictures are allowed</li>
	</ul>
</Container>
<Container>
	<h2>1.5.1</h2>
	<ul>
		<li>When I select my profile picture it seems to load twice</li>
	</ul>
</Container>
<Container>
	<h2>1.5</h2>
	<ul>
		<li>
			Change the style of beta 4 the signal does not move)
		</li>
		<li>full page search</li>
		<li>
			The image is now visible in the file (name [name: https://url]). List of video servers supported by some websites (Meower, Tenor, Scratch, cubeupload, Discord and imgBB).
		</li>
		<li>
			New profile pictures from the <a href="https://bettermeower.app"
				>BetterMeower</a
			> project
		</li>
		<li>Badges now also look nicer and are next to the username now</li>
		<li>Adjusted date styling (no longer underlined, help cursor)</li>
		<li>Fixes to buttons on touchscreens</li>
		<li>Fixed the group chat page expanding with long messages</li>
		<li>Some minor polishing and bugfixes</li>
	</ul>

	<br />

	<details>
		<summary>Betas</summary>
		<h3>Hotfix</h3>
		<ul>
			<li>
				Disable bot badges (they aren't officially supported, and the
				CL4 port will add them)
			</li>
		</ul>

		<h3>Release</h3>
		<ul>
			<li>Banned status</li>
			<li>Reallow reporting posts from verified bots</li>
			<li>Made badges look nicer and put then next to the username</li>
			<li>Fixes to buttons on touchscreens</li>
			<li>Fixed the group chat page expanding with long messages</li>
			<li>Adjusted date styling (no longer underlined, help cursor)</li>
			<li>Disabled several features (rip)</li>
			<li>Updates to images in posts</li>
			<li>Some general polishing and bugfixes</li>
		</ul>

		<h3>Dev Preview 3</h3>
		<ul>
			<li>I don't really know</li>
			<li>Sidebar transition</li>
		</ul>

		<h3>Preview 2.5</h3>
		<ul>
			<li>Added http.meower.org as an allowed image hosting site</li>
			<li>
				Fixed an issue where images will break if they aren't on an
				allowed image hosting site
			</li>
		</ul>

		<h3>Preview 2</h3>
		<ul>
			<li>Added going to a profile by username</li>
			<li>Crash bug fix (hopefully)</li>
			<li>Unfinished mod panel</li>
			<li>Changelog page (this one!)</li>
			<!--
				it's roblox kid
				<li>
					Added "Badge" to Roblox888i for 200th chat (please dont beg for
					badges)
				</li>
			-->
			<li>Search bar only when logged in fix</li>
		</ul>

		<h3>Dev Preview 1</h3>
		<ul>
			<li>Search page</li>
			<li>BetterMeower profile picture support</li>
			<li>Statisics</li>
			<li>Bot tags (verified, unverified, bot owner)</li>
			<li>Don't allow verified bot posts to be reported</li>
			<li>Image links showing as images</li>
		</ul>
	</details>
</Container>
<Container>
	<h2>1.4.2</h2>
	<ul>
		<li>Support webhook posts from @Webhooks bot</li>
	</ul>
</Container>
<Container>
	<h2>1.4.2</h2>
	<ul>
		<li>
			Allow the sidebar to show on mobile (you can restore the old
			behavior by switching to old layout)
		</li>
	</ul>
	(these changes were made before, but are considered part of 1.4.2:)
	<ul>
		<li>Fix an issue that caused posts to sometimes not show up in home</li>
		<li>Add credentials when fetching home (to view pages past 1)</li>
		<li>
			Rename page title from "Meower Svelte" to "Meower" to reflect it
			becoming the official main client
		</li>
	</ul>
</Container>
<Container>
	<h2>1.4.1</h2>
	<ul>
		<li>Fixed posts sometimes not showing up in home</li>
	</ul>
</Container>
<Container>
	<h2>1.4</h2>
	<ul>
		<li>Typing indicators, quotes, and line breaks</li>
		<li>Fixed spam by holding down enter while ratelimited</li>
		<li>Group chat members, adding and removing</li>
		<li>Modals, replies and a bunch of other stuff</li>
	</ul>
</Container>
<Container>
	<h2>1.3</h2>
	<ul>
		<li>Group chats</li>
		<li>Inbox</li>
		<li>Discord Support</li>
	</ul>
</Container>
<Container>
	<h2>1.2</h2>
	<ul><li>Mainly profiles</li></ul>
</Container>
<Container>
	<h2>1.1.2</h2>
	<ul><li>Group cat</li></ul>
</Container>
<Container>
	<h2>1.1</h2>
	<ul>
		<li>Account deletion</li>
		<li>Login saving</li>
		<li>Fixed only being able to log in once per session</li>
		<li>Add TOS/PP confirmation when creating an account</li>
		<li>Fix "Let's go!" text in setup</li>
	</ul>
</Container>
<Container>
	<h2>1.0.1</h2>
	<ul><li>Center login screen</li></ul>
</Container>
<Container>
	<h2>1.0</h2>
	<ul><li>Inital release</li></ul>
</Container>

<style>
	h3 {
		margin-top: 0.5ex;
		margin-bottom: 0.5ex;
	}
</style>
