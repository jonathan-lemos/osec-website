<script lang="ts">
	import './style.sass';

	let active: string = 'home';
	let fadingOut: boolean = false;

	$: active;
	$: fadingOut;

	function sleep(ms: number) {
		return new Promise((resolve, _reject) => {
			setTimeout(resolve, ms);
		});
	}

	async function setActive(s: string) {
		if (s == active) {
			return;
		}

		fadingOut = true;
		await sleep(100);
		fadingOut = false;
		active = s;
	}

  function getSectionClass() {
    return fadingOut ? 'fade-out' : 'fade-in';
  }
</script>

<h1 id="ls-cmd">$ ls osprey_security</h1>
<table id="ls-output">
	<tbody>
		<tr>
			<td><a href="/" on:click={(_) => setActive('about')} class={active === 'about' ? 'active' : ''}>about</a></td>
			<td><a href="/" on:click={(_) => setActive('home')} class={active === 'home' ? 'active' : ''}>home</a></td>
			<td
				><a href="/" on:click={(_) => setActive('resources')} class={active === 'resources' ? 'active' : ''}
					>resources</a
				></td
			>
			<td><a href="https://ctftime.org/event/list/upcoming" target="_blank">ctf time</a></td>
		</tr>
		<tr>
			<td
				><a href="https://unf.campuslabs.com/engage/organization/osec" target="_blank"
					>perch_portal</a
				></td
			>
			<td><a href="https://discord.gg/8AdgjhdvFh" target="_blank">discord</a></td>
			<td><a href="http://unfcyber.org/images/3955024.png" target="_blank">instagram</a></td>
			<td><a href="https://twitter.com/clubosprey" target="_blank">twitter</a></td>
		</tr>
	</tbody>
</table>

{#if active === 'home'}
	<section id="home" class={fadingOut ? 'fade-out' : 'fade-in'}>
		<p>
			Osprey Security is a club with the main focus on Cyber Security and Ethical Hacking. We
			provide a controlled environment where members can learn, experience, and practice varying
			degrees of Cyber Security topics daily. Over the course of a semester members have the
			opportunity to attend workshops or presentations from IT professionals, business leaders, and
			University professors. In addition, we facilitate a committed group of inexperienced and
			experienced members to participate in a wide variety of both local and national Cyber Security
			competitions.
			<br /><br />
			We are always open to new members, and to learn new things, if you have suggestions, or want to
			give a presentation reach out at the about section.
			<br /><br />
			Meeting Time: Friday at 5:30 PM in Building 15
		</p>
	</section>
{:else if active === 'about'}
	<section id="about" class={fadingOut ? 'fade-out' : 'fade-in'}>
		<p>
			Meet the Officers:
			<br />
			<br />
			President: Ben Orensky
			<br />
			Vice President: Scott Jeffrey
			<br />
			Secretary: Wren Billingsley
			<br />
			Treasurer: Connor Geller
			<br />
			Team Capitan: Zachary Whitaker
			<br />
			Event Coordinator: Thang Pham
			<br />
		</p>
	</section>
{:else}
	<p>todo</p>
{/if}
