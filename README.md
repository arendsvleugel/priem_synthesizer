Bouw een zelfstandige interactieve web-synthesizer in één HTML-bestand (met Web Audio API, Tailwind CSS en HTML5 Canvas), strak en zonder overbodige toeters en bellen.



Neem het volgende mee vanaf het begin:

Schuivend 10-priemvenster & interpriemafstand (prime-gap timing):
Gebruik een vooraf berekende lijst met priemgetallen (startend bij 2, 3, 5, 7, 11, 13, 17, 19, 23, 29).
Elke stap schuift 1 priem op: het oudste priemgetal valt af en het volgende priemgetal komt erbij.
De timing van de volgende stap volgt de interpriemafstand (p_{n+1} - p_n) vermenigvuldigd met een instelbare tijdseenheid Δt (standaard 0,25 s, bv. stap 1 -> stap 2 start 3 - 2 = 1 tijdseenheid later).
Inclusief Play/Stop (ook via spatiebalk), Volgende stap, Reset naar #1, Loop en instelbare Glide/Morph (0%–100%).
Boventoon-aftrekking met het laatste priemgetal:
Voor elke priem p in het actieve 10-priemvenster wordt de boventoon-orde afgetrokken met het laatste priemgetal p_last van dat venster (m = max(1, |p_last - p|)), zodat de klank binnen een compact, hoorbaar spectrum blijft.
Voorzie live regelaars voor amplitude en fase (0°–360°) per stem (grondtoon + 10 priemboventonen), plus presets (natuurlijk verval 1/p, gelijke energie 1/√p, gelijke amplitude, alleen priems) en Mute (M) / Solo (S).
Schuivende grondfrequentie (~2 octaven gemiddeld):
Laat de actieve grondfrequentie per stap relatief meebewegen met de interpriemafstand ten opzichte van de gemiddelde priemafstand rond een instelbaar anker (standaard 220 Hz), over een bereik van gemiddeld ongeveer 2 octaven (met zachte compressie zodat uitschieters beheersbaar blijven en met vloeiende overgang via glide).
Robuuste Web Audio & Canvas-visualisaties:
Gebruik een dubbele stem-architectuur (Voice A en Voice B met OscillatorNode + GainNode) en roep cancelScheduledValues() en setValueAtTime() aan voor klikvrije overgangen en een foutloze stop.
Begrens PeriodicWave-tabellen strikt op de Nyquist-frequentie en een veilige buffergrootte (MAX_TABLE_SIZE = 8192) om IndexSizeError of NotSupportedError te voorkomen.
Toon een schuivende tijdlijn met de actieve priemgetallen, onderlinge gaps en frequenties, plus een oscilloscoop (met piekwaarde en crest factor) en een frequentiespectrum (FFT) op HTML5 Canvas.
