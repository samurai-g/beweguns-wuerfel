<script lang="ts">
	import { base, resolve } from '$app/paths';
	import { Download, ExternalLink } from '@lucide/svelte';
	import setImg from '$lib/assets/download/set.jpg';
	import stampfen from '$lib/assets/download/stampfen.png';
	import ball from '$lib/assets/download/ball.png';
	import handFaust from '$lib/assets/download/hand_faust.png';
	import kopf from '$lib/assets/download/kopf.png';
	import armeHochheben from '$lib/assets/download/arme_hochheben.png';
	import klatschen from '$lib/assets/download/klatschen.png';

	const driveFolder = 'https://drive.google.com/drive/folders/1rcmnPR8oewgUZ7-i7twJ92RRg8kScoMu';
	const licenseUrl = 'https://creativecommons.org/licenses/by-sa/4.0/deed.de';

	const files = [
		{
			title: '3D-Modell, Version 6',
			desc: 'Aktuelles Modell als 3MF-Projekt mit den Druckeinstellungen unserer Serie. Öffnen mit Bambu Studio, OrcaSlicer, PrusaSlicer oder Cura.',
			meta: '3MF · 0,4 MB',
			href: '/downloads/BewegUNS-Wuerfel_V6_3D-Druck_Bambu-Studio-Projekt.3mf',
			name: 'BewegUNS-Wuerfel_V6_3D-Druck_Bambu-Studio-Projekt.3mf'
		},
		{
			title: '3D-Modell, Version 1',
			desc: 'Erste Version des Würfels als STL, für jeden Slicer.',
			meta: 'STL · 0,6 MB',
			href: '/downloads/BewegUNS-Wuerfel_V1_3D-Druck.stl',
			name: 'BewegUNS-Wuerfel_V1_3D-Druck.stl'
		},
		{
			title: 'Papiervorlage',
			desc: 'Würfelnetz zum Ausdrucken auf A4: ausschneiden, falten, kleben. Für alle ohne 3D-Drucker.',
			meta: 'JPG · 0,3 MB',
			href: '/downloads/BewegUNS-Wuerfel_Papiervorlage_Ausdrucken-Ausschneiden-Kleben.jpg',
			name: 'BewegUNS-Wuerfel_Papiervorlage_Ausdrucken-Ausschneiden-Kleben.jpg'
		},
		{
			title: 'Spielanleitung',
			desc: 'Das Set, die sechs Bewegungen, das Grundprinzip und die fünf Spielformen mit Varianten und Schwierigkeitsstufen.',
			meta: 'PDF · 3 Seiten · 0,8 MB',
			href: '/downloads/Spielanleitung_BewegUNS-Wuerfel_CC-BY-SA-4.0.pdf',
			name: 'Spielanleitung_BewegUNS-Wuerfel_CC-BY-SA-4.0.pdf'
		},
		{
			title: 'README und Lizenz',
			desc: 'Kurzbeschreibung aller Dateien, Hinweise zum Druck und der Lizenztext.',
			meta: 'TXT',
			href: '/downloads/README_BewegUNS-Wuerfel_Open-Source.txt',
			name: 'README_BewegUNS-Wuerfel_Open-Source.txt'
		}
	] as const;

	const symbols = [
		{ title: 'Stampfen', img: stampfen, file: 'Symbol_Stampfen.svg' },
		{ title: 'Ball weitergeben', img: ball, file: 'Symbol_Ball.svg' },
		{ title: 'Faust', img: handFaust, file: 'Symbol_Hand-Faust.svg' },
		{ title: 'Kopf bewegen', img: kopf, file: 'Symbol_Kopf.svg' },
		{ title: 'Arme hochheben', img: armeHochheben, file: 'Symbol_Arme-Hochheben.svg' },
		{ title: 'Klatschen', img: klatschen, file: 'Symbol_Klatschen.svg' }
	] as const;
</script>

<svelte:head>
	<title>Selbst drucken - BewegUNS-Würfel</title>
	<meta
		name="description"
		content="Der BewegUNS-Würfel ist Open Source: 3D-Druckdateien, Symbole, Papiervorlage und Spielanleitung zum Download unter CC BY-SA 4.0."
	/>
</svelte:head>

<article class="space-y-20">
	<section class="flex flex-col items-center gap-10 lg:flex-row">
		<div class="flex-1 space-y-4">
			<h1 class="text-3xl font-bold">Selbst drucken</h1>
			<p>
				Der BewegUNS-Würfel ist Open Source. Wer einen 3D-Drucker hat oder ein FabLab, eine Schule
				oder eine Werkstatt mit Drucker kennt, kann sich den Würfel selbst drucken. Wer keinen
				Drucker hat, bastelt ihn aus Papier. Die Spielformen funktionieren mit jedem Würfel, auf dem
				die sechs Bewegungen stehen.
			</p>
			<p>
				Alle Dateien stehen unter der Lizenz
				<a
					href={licenseUrl}
					target="_blank"
					rel="noopener noreferrer license"
					class="hover:text-primary-700 underline underline-offset-4">CC BY-SA 4.0</a
				>. Nutzen, teilen und verändern ist erlaubt, wenn ihr uns nennt und Bearbeitungen unter
				derselben Lizenz weitergebt.
			</p>
		</div>
		<div class="flex flex-1 justify-center">
			<img
				src={setImg}
				alt="Das BewegUNS-Würfel-Set: Box, Bewegungswürfel, Zahlenwürfel und Spielkarten"
				class="h-64 w-auto rounded-xl object-contain shadow-lg lg:h-80"
			/>
		</div>
	</section>

	<section class="space-y-6">
		<h2 class="text-2xl font-bold">Dateien zum Download</h2>
		<ul class="divide-y divide-slate-200 border-y border-slate-200">
			{#each files as file (file.name)}
				<li class="flex flex-col gap-4 py-5 sm:flex-row sm:items-center">
					<div class="flex-1 space-y-1">
						<h3 class="font-bold">{file.title}</h3>
						<p class="text-slate-700">{file.desc}</p>
						<p class="text-sm text-slate-500">{file.meta}</p>
					</div>
					<a
						href={`${base}${file.href}`}
						download={file.name}
						class="text-primary-700 hover:bg-primary-50 border-primary-700 focus-visible:ring-primary-700 inline-flex items-center gap-2 self-start rounded-lg border-2 bg-white px-5 py-2 font-medium shadow-sm transition-colors focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:outline-none sm:self-center"
					>
						<Download size={20} aria-hidden="true" />
						Herunterladen
					</a>
				</li>
			{/each}
		</ul>
		<p>
			<a
				href={driveFolder}
				target="_blank"
				rel="noopener noreferrer"
				class="hover:text-primary-700 inline-flex items-center gap-2 underline underline-offset-4"
			>
				<ExternalLink size={18} aria-hidden="true" />
				Alle Dateien als Ordner auf Google Drive
			</a>
		</p>
	</section>

	<section class="space-y-6">
		<div class="space-y-4">
			<h2 class="text-2xl font-bold">Die sechs Symbole</h2>
			<p>
				Die Symbole der sechs Würfelseiten als Vektorgrafik (SVG), zum Beispiel für eigene
				Spielkarten, Plakate oder einen Würfel aus Holz oder Schaumstoff.
			</p>
		</div>
		<ul class="grid grid-cols-2 gap-4 sm:grid-cols-3 lg:grid-cols-6">
			{#each symbols as symbol (symbol.file)}
				<li>
					<a
						href={`${base}/downloads/${symbol.file}`}
						download={symbol.file}
						class="group hover:border-primary-700 focus-visible:ring-primary-700 flex flex-col items-center gap-3 rounded-xl border border-slate-200 bg-white p-4 transition focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:outline-none"
					>
						<img src={symbol.img} alt="" class="h-24 w-24 object-contain" />
						<span class="text-center text-sm font-medium">{symbol.title}</span>
						<span class="sr-only">als SVG herunterladen</span>
					</a>
				</li>
			{/each}
		</ul>
	</section>

	<section class="space-y-6">
		<h2 class="text-2xl font-bold">So kommt der Würfel zu dir</h2>
		<div class="grid grid-cols-1 gap-6 lg:grid-cols-3">
			<section class="space-y-3 rounded-xl bg-slate-50 p-6">
				<div class="text-primary-700 text-4xl font-bold">1</div>
				<h3 class="font-bold">Datei laden</h3>
				<p>
					Das 3MF-Projekt enthält Modell und Druckeinstellungen. Die STL-Datei ist die Rohform für
					jeden Slicer.
				</p>
			</section>
			<section class="space-y-3 rounded-xl bg-slate-50 p-6">
				<div class="text-primary-700 text-4xl font-bold">2</div>
				<h3 class="font-bold">Drucken</h3>
				<p>
					Der Würfel ist hohl, damit er leicht ist und Material spart. Die Symbole sind erhaben und
					lassen sich ertasten. Kontrastreiche Farben helfen beim Erkennen, bei uns Pink und
					Schwarz.
				</p>
			</section>
			<section class="space-y-3 rounded-xl bg-slate-50 p-6">
				<div class="text-primary-700 text-4xl font-bold">3</div>
				<h3 class="font-bold">Spielen</h3>
				<p>
					Die Spielanleitung erklärt fünf Spielformen für 4 bis 12 Personen. Ohne Drucker:
					Papiervorlage ausdrucken, ausschneiden, kleben, losspielen.
				</p>
			</section>
		</div>
	</section>

	<section class="space-y-4 rounded-2xl bg-slate-50 p-8">
		<h2 class="text-2xl font-bold">Lizenz: CC BY-SA 4.0</h2>
		<p>
			Ihr dürft die Dateien vervielfältigen, weitergeben, verändern und darauf aufbauen, auch für
			kommerzielle Zwecke. Zwei Bedingungen: Nennt „BewegUNS-Würfel, www.beweg-uns-wuerfel.at“ als
			Quelle und gebt Bearbeitungen unter derselben Lizenz weiter.
		</p>
		<p class="text-sm text-slate-700">
			Empfohlene Quellenangabe: „BewegUNS-Würfel“ von der informellen Gruppe BewegUNS-Würfel, Graz,
			www.beweg-uns-wuerfel.at, lizenziert unter
			<a
				href={licenseUrl}
				target="_blank"
				rel="noopener noreferrer license"
				class="hover:text-primary-700 underline underline-offset-4">CC BY-SA 4.0</a
			>.
		</p>
		<p class="text-sm text-slate-700">
			Entwickelt mit Menschen mit und ohne Behinderungen in drei inklusiven Workshops in Graz,
			gefördert vom Europäischen Solidaritätskorps der Europäischen Union.
		</p>
	</section>

	<section class="space-y-4">
		<h2 class="text-2xl font-bold">Zeig uns dein Ergebnis</h2>
		<p>
			Du hast den Würfel gedruckt, gebastelt oder in deiner Gruppe gespielt? Schick uns ein Foto
			oder erzähl uns, wie es gelaufen ist. Für Gruppen von 6 bis 30 Personen bieten wir Workshops
			an.
		</p>
		<a
			href={resolve('/kontakt')}
			class="bg-primary-700 hover:bg-primary-600 focus-visible:ring-primary-700 inline-block rounded-lg px-8 py-3 font-medium text-white transition-colors focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:outline-none"
		>
			Kontakt aufnehmen
		</a>
	</section>
</article>
