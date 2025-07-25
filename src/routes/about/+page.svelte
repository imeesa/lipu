<script lang="ts">
	import {
		Accordion,
		AccordionContent,
		AccordionItem,
		AccordionTrigger,
	} from "$lib/components/ui/accordion";
	import { Button } from "$lib/components/ui/button";
	import WebIcon from "~icons/lucide/globe";
	import LanguagesIcon from "~icons/lucide/languages";
	import SurveyIcon from "~icons/lucide/list-checks";
	import TableIcon from "~icons/lucide/table-2";
	import RobotIcon from "~icons/mdi/robot-excited";
	import DiscordIcon from "~icons/simple-icons/discord";

	let openAccordion = $state<string>();
</script>

<svelte:head>
	<title>lipu Linku &middot; About Linku</title>
</svelte:head>

<main class="py-4 md:my-auto flex flex-col items-center justify-center gap-4 min-h-full">
	<h1 class="font-medium text-4xl">About Linku</h1>

	<p class="*:[button]:underline px-4 md:w-[max(65%,600px)] text-center text-balance">
		Linku is a <button onclick={() => (openAccordion = "dataset")}>dataset</button> with many
		<button onclick={() => (openAccordion = "translations")}>translations</button>, a
		<button onclick={() => (openAccordion = "bot")}>Discord bot</button>, a
		<button onclick={() => (openAccordion = "website")}>website</button>, and an
		<button onclick={() => (openAccordion = "survey")}>annual survey</button> created by kala Asi and
		contributed to by jan Ke Tami, jan Telesi, jan Kekan San, and many others for the purpose of collecting
		and displaying toki pona dictionary information accurate to current use.
	</p>

	<p>
		ku data is provided by
		<a
			class="underline"
			href="http://tokipona.org/nimi_pu.txt"
			target="_blank"
			rel="noopenner noreferrer"
		>
			tokipona.org
		</a>.
	</p>

	<Accordion
		type="single"
		bind:value={openAccordion}
		class="
		px-6 w-full md:w-[max(65%,600px)] **:[a,button]:cursor-pointer **:[a,button]:not-data-button-root:not-data-accordion-trigger:underline 
		**:data-bits-accordion-content:*:[div]:flex **:data-bits-accordion-content:*:[div]::flex-col
		**:data-bits-accordion-content:*:[div]:gap-3
	"
	>
		<AccordionItem value="dataset">
			<AccordionTrigger>
				<span class="flex items-center gap-3">
					<TableIcon /> sona Linku (the dataset)
				</span>
			</AccordionTrigger>
			<AccordionContent>
				<p>
					The <a href="https://github.com/lipu-linku/sona">dataset</a> is a github repository which has
					all data we track, and is where you go to add new data. Everyone may view the data, but direct
					contributions are only available to maintainers or via pull requests.
				</p>
				<p>
					Changes to the source language data are automatically synced to
					<button onclick={() => (openAccordion = "translations")}>Crowdin</button>, and changes to
					Crowdin translations are automatically synced to the dataset. Subsequently, all data in
					the dataset is made available via the API hosted alongside
					<button onclick={() => (openAccordion = "website")}>the website</button>.
				</p>
				<p>
					The <a href="https://github.com/lipu-linku">Linku github organization</a> is owned by kala
					Asi and jan Kekan San, and changes are discussed in
					<a href="https://discord.gg/A3ZPqnHHsy" target="_blank" rel="noopener noreferrer"
						>kulupu Linku</a
					>.
				</p>
				<p>
					If you are looking for the old dataset called jasima, the data can be found
					<a href="https://linku.la/jasima/data.json" target="_blank" rel="noopener noreferrer"
						>here</a
					>
					and the repo can be found
					<a href="https://github.com/lipu-linku/jasima" target="_blank" rel="noopener noreferrer"
						>here</a
					>. Also see
					<button onclick={() => (openAccordion = "translations")}>nimi Linku</button> for information
					about the previous Google sheet.
				</p>
			</AccordionContent>
		</AccordionItem>
		<AccordionItem value="bot">
			<AccordionTrigger>
				<span class="flex items-center gap-3">
					<RobotIcon /> ilo Linku (the bot)
				</span>
			</AccordionTrigger>
			<AccordionContent
				class="*:[div]:space-y-4 **:[code]:border **:[code]:border-border **:[code]:px-1 **:[code]:rounded-sm"
			>
				<p>
					The bot is for requesting and receiving Linku data without leaving discord, with a couple
					quality of life features.
				</p>
				<Button
					variant="secondary"
					href="https://discord.com/oauth2/authorize?client_id=901910020701163522&permissions=277025441792&scope=applications.commands%20bot"
				>
					Add it to your server!
				</Button>

				<h2>
					<code>/nimi</code> (<code>/n</code>)
				</h2>
				<p>
					Returns a dictionary entry on the word you requested.
					<br />
					You can customise the language used for the definitions using
					<code>/preferences language</code> (the default is English).
				</p>

				<h2><code>/ss</code></h2>
				<p>Returns the sitelen sitelen (sitelen suwi) glyph for the word you requested.</p>

				<h2><code>/lp</code></h2>
				<p>Returns a luka pona sign gif for the word you requested.</p>

				<h2><code>/sp</code></h2>
				<p>
					Converts your text to the linja sike font for sitelen pona, and displays it as an image.
					<br />
					You can customise the size of the font using
					<code>/preferences fontsize</code> (the default is 72).
				</p>

				<h2><code>/acro</code></h2>
				<p>
					Finds toki pona words beginning with each letter in your request.<br />
					You can customise the set of words (only pu/pu and ku suli/pu and ku/all available words) will
					be used using
					<code class="whitespace-nowrap">/preferences acro</code> (the default is pu and ku suli).
				</p>

				<h2><code>/prompt</code></h2>
				<p>
					Provides a random conversation prompt in Toki Pona, with a translation in your set
					language or English under a spoiler.
				</p>

				<h2><code>/preferences</code></h2>
				<p>
					Its uses are listed above.<br />
					Additionally, you can reset all preferences using
					<code>/preferences reset</code>.
				</p>
			</AccordionContent>
		</AccordionItem>
		<AccordionItem value="translations">
			<AccordionTrigger>
				<span class="flex items-center gap-3">
					<LanguagesIcon /> nimi Linku (the translations)
				</span>
			</AccordionTrigger>
			<AccordionContent>
				<p>
					kulupu Linku has an <a
						href="https://nimi.linku.la/"
						target="_blank"
						rel="noopener noreferrer">instance</a
					>
					on
					<a href="https://crowdin.com">Crowdin</a>, a localization platform, where anyone can help
					translate data in our dataset. We support translating definitions, etymology of words,
					etymology of sitelen pona, and commentary.
				</p>
				<p>
					If there are any changes on Crowdin, such as approved translations or newly available
					languages, they are automatically mirrored to
					<button onclick={() => (openAccordion = "dataset")}>the dataset</button>. This also works
					in reverse; changes to the dataset are mirrored to Crowdin, including changes to source
					data.
				</p>
				<p>
					Our Crowdin instance is managed by jan Kekan San, kala Asi, and jan Tepo, with specific
					languages managed by many others.
				</p>

				<p>
					Contributions to existing languages are open to anyone; corrections, new languages, and
					other work are discussed in
					<a href="https://discord.gg/A3ZPqnHHsy">kulupu Linku</a>.
				</p>
				<p>
					If you're looking for the Google sheet previously named nimi Linku, it can be found
					<a
						href="https://docs.google.com/spreadsheets/d/1xwgTAxwgn4ZAc4DBnHte0cqta1aaxe112Wh1rv9w5Yk"
					>
						here
					</a>. Note that it has been archived and cannot be contributed to any longer.
				</p>
			</AccordionContent>
		</AccordionItem>
		<AccordionItem value="website">
			<AccordionTrigger>
				<span class="flex items-center gap-3">
					<WebIcon /> lipu Linku (the website)
				</span>
			</AccordionTrigger>
			<AccordionContent>
				<p>
					The <a href="/">website</a> is for browsing the dictionary in a nicely presented/filtered way.
				</p>
				<p>
					The data is loaded from the
					<button onclick={() => (openAccordion = "dataset")}>sona dataset</button>.
				</p>
				<p>
					You may choose the language you want definitions to use, and filter by the words'
					appearances in books and usage among the toki pona community.
				</p>
				<p>
					The website is available as free, open source software, under the GPL-3 license. It is
					built using <a href="https://svelte.dev/" target="_blank" rel="noopener noreferrer">
						SvelteKit
					</a>,
					<a href="https://tailwindcss.com/" target="_blank" rel="noopener noreferrer"
						>tailwindcss</a
					>
					, and
					<a href="https://www.shadcn-svelte.com/" target="_blank" rel="noopener noreferrer">
						shadcn-svelte
					</a>.
				</p>
			</AccordionContent>
		</AccordionItem>
		<AccordionItem value="survey">
			<AccordionTrigger>
				<span class="flex items-center gap-3">
					<SurveyIcon /> wile Linku (the survey)
				</span>
			</AccordionTrigger>
			<AccordionContent class="*:[div]:space-y-3">
				<p>
					The survey is run annually every
					<a href="https://suno.pona.la" target="_blank" rel="noopener noreferrer"
						>suno pi toki pona</a
					>, anniversary of Toki Pona, and asks the community how they use Toki Pona and the words
					in it.
				</p>
				<p>
					This data is used to fill out <button onclick={() => (openAccordion = "dataset")}
						>the dataset</button
					>
					with up to date information about how Toki Pona is used, to make the Linku dictionary provided
					by <button onclick={() => (openAccordion = "website")}>the website</button> and
					<button onclick={() => (openAccordion = "bot")}>the Discord bot</button> as accurate as possible.
				</p>
				<p>
					The survey is distributed via Google forms, and its execution and analysis are discussed
					in
					<a href="https://discord.gg/A3ZPqnHHsy" target="_blank" rel="noopener noreferrer"
						>kulupu Linku</a
					>.
				</p>

				<Button
					href="https://github.com/lipu-linku/ijo/blob/main/survey/2024/README.md"
					target="_blank"
					rel="noopener noreferrer"
					class="whitespace-nowrap"
					variant="secondary"
				>
					See the 2024 Word Survey results here!
				</Button>
			</AccordionContent>
		</AccordionItem>
	</Accordion>

	<Button
		variant="secondary"
		href="https://discord.gg/A3ZPqnHHsy"
		target="_blank"
		rel="noopener noreferrer"
		class="flex items-center gap-[1ch]"
	>
		<DiscordIcon /> kulupu Linku on Discord
	</Button>

	<p class="px-4 md:w-[max(65%,600px)] text-center text-balance">
		Also, check out <a
			class="underline"
			href="https://nimi.li"
			target="_blank"
			rel="noopener noreferrer">nimi.li</a
		>, a third party frontend for sona Linku created by ijo Tani, and
		<a
			class="underline"
			href="https://lipamanka.gay/essays/dictionary/"
			target="_blank"
			rel="noopener noreferrer">lipamanka's dictionary</a
		>, which defines words based on their semantic space.
	</p>
</main>
