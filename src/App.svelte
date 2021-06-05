<script>
	import {user} from "./sessionStore"
	import {supabase} from "./supabaseClient"
	import Auth from "./Auth.svelte"
	import Profile from "./Profile.svelte"

	user.set(supabase.auth.user())

	supabase.auth.onAuthStateChange((_, session) => {
		user.set(session.user)
	})
</script>

<div class="container" style="padding: 50px 0 100px 0;">
	{#if $user}
			<Profile />
	{:else}
			<Auth />
	{/if}
</div>