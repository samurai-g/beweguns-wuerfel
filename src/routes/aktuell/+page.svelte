<script>
	import { resolve } from '$app/paths';
	import { Printer } from '@lucide/svelte';
</script>

<svelte:head>
	<title>Aktuell - BewegUNS-Würfel</title>
</svelte:head>

<section class="mb-12">
	<h1 class="text-3xl font-bold mb-6">Aktuell</h1>

	<div class="bg-slate-50 border-t-4 border-accent-500 rounded-lg shadow-md p-6 mb-8 flex flex-col gap-4">
		<h2 class="text-2xl font-bold">Neu: Der Würfel zum Selbstdrucken</h2>
		<p class="text-gray-700">
			Die 3D-Druckdateien, die sechs Symbole, eine Papiervorlage und die Spielanleitung stehen ab sofort
			als Open Source unter CC BY-SA 4.0 zum Download. Wer einen 3D-Drucker hat, kann sich den
			BewegUNS-Würfel selbst drucken. Wer keinen hat, bastelt ihn aus Papier.
		</p>
		<a
			href="{resolve('/download')}"
			class="inline-flex items-center gap-2 bg-white text-primary-700 hover:bg-primary-50 border-2 border-primary-700 py-3 px-6 rounded-lg transition-colors font-medium shadow-sm self-start"
		>
			<Printer size={20} />
			Zu den Druckdateien
		</a>
	</div>
</section>

<!-- Hero Greeting Section -->
<section class="text-center py-16 bg-gray-50  rounded-lg mt-16 mb-16">
	<div class="max-w-2xl mx-auto px-8">
		<h2 class="text-3xl font-bold text-gray-800  mb-6">
			Willkommen bei BewegUNS-Würfel!
		</h2>
		<p class="text-lg text-gray-700 mb-8">
			Wir sind der Meinung, dass jeder Mensch Spaß an Bewegung haben kann!
			Der BewegUNS-Würfel ist ein inklusives Würfelspiel für alle. Er wurde partizipativ entwickelt, also von Menschen
			mit und ohne Behinderungen gemeinsam. So vielfältig wie wir Menschen sind, haben auch die kleinen Spielwürfel
			keine Grenzen. Entdecke verschiedene Spielformen für alt und jung, egal ob unterwegs mit Freunden oder allein
			zuhause - wir bringen Bewegung in deinen Alltag!
		</p>
		<a href="{resolve('/kontakt')}"
			 class="inline-block bg-primary-700 hover:bg-primary-600 text-white py-3 px-8 rounded-lg transition-colors font-medium">
			Kontakt aufnehmen
		</a>
	</div>
</section>
