<script lang="ts">
    import { currentUser,pb } from './pocketbase'

    let username: string;
    let password: string;

    async function login() {
        await pb.collection('users').authWithPassword(username,password);
    }

    async function signUp() {
        try {
            const data ={
                username,
                password,
                passwordConfirm: password,
                name: 'hi mom',
            };
            const createdUser = await pb.collection('users').create(data);
            await login();
        } catch (err) {
            console.error(err)
        }
    }
</script>

{#if $currentUser}
    <p>
        Signed in as {$currentUser.username}
    </p>
{:else}
<form on:submit|preventDefault>
    <input
        class="w-52 broder-2"
        placeholder="Username"
        type="text"
        bind:value={username}
    />
    <input
        placeholder="Password"
        type="text"
        bind:value={password}
    />
    <button on:click={login}>Login</button>
    <button on:click={signUp}>Sign Up</button>
</form>
{/if}