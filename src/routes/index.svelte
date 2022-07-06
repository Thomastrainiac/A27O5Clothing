<!-- <script context="module">
	export const prerender = true;
</script> -->

<script>
	async function handleClick() {
		const webhookBody = {
          embeds: [{
            title: 'Clothing Submitted',
            fields: [
			  { name: 'Department Name:', value: document.getElementById("name").value },
              { name: 'Role:', value: document.getElementById("role").value },
              { name: 'Shirt:', value: document.getElementById("shirt").value },
			  { name: 'Pants:', value: document.getElementById("pants").value }
            ],
			description: document.getElementById("comm").value
          }],
        };

        const webhookUrl = 'https://discord.com/api/webhooks/994057328540254238/-CKax-GiPbgBEplwF2ZzwGunRjqPNfV-5QRC9l-mCkIth35kxPLKos2O4IYjxFols1gB';

        const response = await fetch(webhookUrl, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(webhookBody),
        });

        if (response.ok) {
		  document.getElementById("name").value = "";
		  document.getElementById("role").value = "";
		  document.getElementById("shirt").value = "";
		  document.getElementById("pants").value = "";
		  document.getElementById("comm").value = "";
		  document.getElementById("subForm").style.display = "none"
		  document.getElementById("subDiv").style.display = "none"
		  document.getElementById("completed").style.display = "flex"
		  setTimeout(() => {
			document.getElementById("completed").style.display = "none"
			document.getElementById("subForm").style.display = "flex"
		    document.getElementById("subDiv").style.display = "flex"
		  }, 3000)
        } else {
          alert('There was an error! Try again later!');
        };
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Bulk Games Area 27" />
</svelte:head>

<section>
	<form id="subForm">
		<label for="name">DEPARTMENT NAME:</label><br>
		<input class="name" type="text" id="name" name="name"><br>
		<label for="role">ROLE FOR CLOTHING:</label><br>
		<input class="name" type="text" id="role" name="role"><br>
		<label for="shirt">SHIRT LINK:</label><br>
		<input class="name" type="text" id="shirt" name="shirt"><br>
		<label for="pants">PANTS LINK:</label><br>
		<input class="name" type="text" id="pants" name="pants"><br>
		<label for="comm">COMMENTS (IF ANY):</label><br>
		<textarea class="desc" id="comm" name="comm" rows="4" cols="50" ></textarea><br>
	</form>
	<div id="subDiv">
		<button on:click={handleClick}>
			SUBMIT
		</button>
	</div>
	<div class="completed" id="completed">
		<p>Suggestion Sent</p>
	</div>
</section>

<style>

	form {
		display: flex;
		flex-direction: column;
		padding-left: 10%;
		padding-right: 10%;
	}

	label {
		font-size: 26px;
		font-weight: 700;
	}

	input.name {
		width: 100%;
		border-radius: 5px;
		border: 2px solid rgb(0,117,176);
	}

	textarea.desc {
		width: 100%;
		height: 20vh;
		border-radius: 5px;
		border: 2px solid rgb(0,117,176);
		font-size: 18px;
		resize: none;
	}

	div {
		display: flex;
		padding-left: 10%;
		padding-right: 10%;
		width:100%;
	}

	div.completed {
		display: none;
		justify-content: center;
		padding-left: 0;
		padding-right: 0;
		height: 100vh;
	}

	p {
		margin: 0;
		font-weight: 700;
		font-size: 30px;
		position: absolute;
		top: 50%;
	}
	button {
		width: 20%;
		border-radius: 5px;
		color: white;
		font-weight: 700;
		background-color: rgb(0,117,176);
		border: 3px solid rgb(0,117,176);
		transition: all 0.5s ease;
	}

	button:hover {
		background-color: rgb(255,255,255);
		color: black;
	}

</style>
