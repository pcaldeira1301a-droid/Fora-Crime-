<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Safe Community</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@600;700&family=Figtree:wght@400;500;600;700&family=Patrick+Hand&display=swap" rel="stylesheet">
<style>
  [hidden] { display: none !important; }
  :root {
    --bg: #fbe3b4;
    --frame: #f0a63a;
    --panel: #f4faf8;
    --surface: #ffffff;
    --fg: #16262b;
    --muted: #46606a;
    --teal: #17796a;
    --mint: #cfeee3;
    --violet: #4437c9;
    --yellow: #f2b705;
    --line: #5db69d;
    --pin: #2f6fd6;
    --on-teal: #ffffff;
    --shadow: rgba(20, 38, 43, .25);
    --font-display: "Chakra Petch", "Trebuchet MS", system-ui, sans-serif;
    --font-body: "Figtree", system-ui, -apple-system, "Segoe UI", sans-serif;
    --font-hand: "Patrick Hand", "Comic Sans MS", cursive;
  }
  @media (prefers-color-scheme: dark) {
    :root:not([data-theme="light"]) {
      --bg: #1e1608;
      --frame: #c98421;
      --panel: #13262a;
      --surface: #1a3237;
      --fg: #e8f3f0;
      --muted: #a2bcb6;
      --teal: #2fae98;
      --mint: #1c4039;
      --violet: #aaa2ff;
      --yellow: #f5c542;
      --line: #3a7d6e;
      --pin: #6c9cf5;
      --on-teal: #0e1b1e;
      --shadow: rgba(0, 0, 0, .5);
      color-scheme: dark;
    }
  }
  :root[data-theme="dark"] {
    --bg: #1e1608;
    --frame: #c98421;
    --panel: #13262a;
    --surface: #1a3237;
    --fg: #e8f3f0;
    --muted: #a2bcb6;
    --teal: #2fae98;
    --mint: #1c4039;
    --violet: #aaa2ff;
    --yellow: #f5c542;
    --line: #3a7d6e;
    --pin: #6c9cf5;
    --on-teal: #0e1b1e;
    --shadow: rgba(0, 0, 0, .5);
    color-scheme: dark;
  }

  * { box-sizing: border-box; }
  body {
    margin: 0;
    background: var(--bg);
    color: var(--fg);
    font-family: var(--font-body);
    font-size: 17px;
    line-height: 1.55;
    padding-block: 24px 36px;
    padding-left: max(16px, env(safe-area-inset-left, 0px));
    padding-right: max(16px, env(safe-area-inset-right, 0px));
  }
  h1, h2, h3, p, ul, ol, dl, dd, figure { margin: 0; }
  h1, h2, h3 { font-family: var(--font-display); text-wrap: balance; line-height: 1.1; }
  a:focus-visible { outline: 3px solid var(--yellow); outline-offset: 3px; }
  svg { display: block; max-width: 100%; }

  .frame {
    max-width: 1060px; margin: 0 auto;
    background: var(--frame); border-radius: 26px; padding: 14px;
    box-shadow: 0 18px 40px -18px var(--shadow);
  }
  .poster {
    position: relative; background: var(--panel); border-radius: 16px;
    padding: 34px clamp(18px, 4vw, 44px) 30px;
    display: grid; gap: 26px;
  }
  .poster::before, .poster::after {
    content: ""; position: absolute; top: 14px; width: 14px; height: 14px; border-radius: 50%;
    background: var(--pin); box-shadow: inset -2px -2px 0 rgba(0,0,0,.25);
  }
  .poster::before { left: 14px; }
  .poster::after { right: 14px; }

  .top { display: grid; gap: 12px; justify-items: center; text-align: center; }
  .tag {
    display: inline-flex; align-items: center; gap: 10px; flex-wrap: wrap; justify-content: center;
    background: var(--teal); color: var(--on-teal); border-radius: 6px; padding: 8px 18px;
    font-family: var(--font-display); font-weight: 600; letter-spacing: .08em; text-transform: uppercase; font-size: 14px;
  }
  .tag svg { width: 20px; height: 20px; flex: none; }
  .tag span { font-weight: 400; text-transform: none; letter-spacing: .02em; opacity: .9; }
  .top h1 {
    color: var(--violet); text-transform: uppercase; letter-spacing: .01em;
    font-size: clamp(1.9rem, 6.6vw, 3.6rem);
  }
  .top .sub { font-size: clamp(1.05rem, 2.4vw, 1.3rem); color: var(--muted); max-width: 44ch; }

  .eyebrow {
    font-family: var(--font-display); font-weight: 700; text-transform: uppercase; letter-spacing: .05em;
    color: var(--violet); font-size: 1rem; margin-bottom: 14px;
  }

  .grid { display: grid; grid-template-columns: 1.1fr 1fr; gap: 34px; align-items: start; }
  .grid > * { min-width: 0; }
  @media (max-width: 820px) { .grid { grid-template-columns: 1fr; } }

  .ideas { list-style: none; padding: 0; display: grid; gap: 14px; }
  .ideas li { display: grid; grid-template-columns: 34px 1fr; gap: 12px; align-items: start; }
  .ideas .n {
    font-family: var(--font-display); font-weight: 700; font-size: 1.9rem; line-height: 1; color: var(--teal);
  }
  .ideas b { font-weight: 700; }

  .mapfig { position: relative; margin: 30px 0 70px; }
  .map { border-radius: 4px; overflow: hidden; box-shadow: 0 8px 20px -10px var(--shadow); }
  .map svg { width: 100%; height: auto; }
  .maplabel {
    position: absolute; left: 0; bottom: 0; background: #1a1f22; color: #fff;
    font-family: var(--font-display); font-weight: 600; font-size: 15px; letter-spacing: .03em;
    padding: 7px 18px;
  }
  .zoom {
    position: absolute; right: 4%; bottom: -54px; width: min(34%, 170px); aspect-ratio: 1;
    border-radius: 50%; border: 5px solid #fff; overflow: hidden; box-shadow: 0 10px 22px -8px var(--shadow);
    background: #67b05a;
  }
  .zoom svg { width: 100%; height: 100%; }
  .zoomlabel {
    position: absolute; right: calc(4% + min(34%, 170px) / 2); bottom: -76px; transform: translateX(50%);
    background: var(--surface); color: var(--fg); border: 1.5px solid var(--fg);
    font-size: 14px; font-weight: 600; padding: 1px 10px; white-space: nowrap;
  }

  .right { display: grid; gap: 22px; }
  .event {
    position: relative; background: var(--mint); padding: 16px 20px 18px; text-align: center; display: grid; gap: 4px;
    font-family: var(--font-hand); font-size: 1.3rem; line-height: 1.3;
  }
  .event .label {
    font-family: var(--font-display); font-weight: 700; text-transform: uppercase; letter-spacing: .05em;
    font-size: 1rem; line-height: 1.2;
  }
  .chip {
    justify-self: center; font-family: var(--font-body); font-weight: 600; font-size: 12px;
    background: var(--yellow); color: #1b1600; padding: 2px 10px; border-radius: 99px;
  }
  .arrow {
    position: absolute; left: -52px; top: -28px; width: 54px; height: 54px; color: var(--yellow);
  }
  @media (max-width: 820px) { .arrow { display: none; } }

  .why {
    border: 3.5px dotted var(--line); border-radius: 22px; padding: 22px; display: grid; gap: 14px;
  }
  .why h2 { font-size: clamp(1.3rem, 3.2vw, 1.7rem); }
  .why .photo { border-radius: 6px; overflow: hidden; }
  .why .photo svg { width: 100%; height: auto; }
  .why ul { list-style: none; padding: 0; display: grid; gap: 8px; }
  .why li { display: grid; grid-template-columns: 14px 1fr; gap: 8px; }
  .why li::before { content: "•"; font-weight: 700; color: var(--teal); }

  .message {
    font-family: var(--font-display); font-weight: 700; text-transform: uppercase; letter-spacing: .03em;
    color: var(--violet); font-size: 1.1rem; text-align: center; line-height: 1.3;
  }

  .closing {
    text-align: center; color: var(--violet); text-transform: uppercase; letter-spacing: .02em;
    font-size: clamp(1.4rem, 4.6vw, 2.4rem); padding-top: 4px;
  }

  .contact { text-align: center; color: var(--muted); font-size: 15px; display: grid; gap: 4px; }
  .contact strong { color: var(--fg); }

  .btn {
    appearance: none; font: inherit; font-weight: 700; cursor: pointer; text-decoration: none;
    display: inline-flex; align-items: center; justify-content: center; gap: 8px; min-height: 44px;
    border-radius: 10px; padding: 10px 18px; border: 2px solid var(--teal); background: var(--teal); color: var(--on-teal);
  }
  .btn.alt { background: transparent; color: var(--teal); }
  .btn:focus-visible { outline: 3px solid var(--yellow); outline-offset: 3px; }
  .btn[disabled], .btn[aria-disabled="true"] { opacity: .5; cursor: not-allowed; }
  .btn svg { width: 20px; height: 20px; flex: none; }
  .sr { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }

  .hintline { font-size: 15px; color: var(--muted); margin: -4px 0 14px; }
  .ideas li { display: block; }
  .idea {
    appearance: none; width: 100%; text-align: left; cursor: pointer; font: inherit; color: var(--fg);
    display: grid; grid-template-columns: 34px 1fr auto; gap: 12px; align-items: center;
    background: var(--surface); border: 2px solid var(--line); border-radius: 14px; padding: 12px 14px;
    transition: transform .15s ease, border-color .15s ease;
  }
  .idea:hover { border-color: var(--violet); transform: translateY(-1px); }
  .idea:focus-visible { outline: 3px solid var(--yellow); outline-offset: 3px; }
  .idea .go {
    font-family: var(--font-display); font-weight: 700; font-size: .78rem; text-transform: uppercase;
    letter-spacing: .05em; color: var(--violet); white-space: nowrap;
  }
  @media (max-width: 560px) { .idea { grid-template-columns: 34px 1fr; } .idea .go { grid-column: 2; } }
  @media (prefers-reduced-motion: reduce) { .idea { transition: none; } .idea:hover { transform: none; } }

  .rotate {
    display: none; position: fixed; inset: 0; z-index: 100; background: var(--bg); color: var(--fg);
    place-content: center; justify-items: center; gap: 16px; text-align: center;
    padding: max(24px, env(safe-area-inset-top, 0px)) max(20px, env(safe-area-inset-right, 0px)) max(24px, env(safe-area-inset-bottom, 0px)) max(20px, env(safe-area-inset-left, 0px));
  }
  .rotate h2 { font-size: clamp(1.7rem, 8vw, 2.4rem); color: var(--violet); text-transform: uppercase; }
  .rotate p { max-width: 28ch; color: var(--muted); }
  .rotate svg { width: 120px; height: 120px; color: var(--teal); animation: girar 2.8s ease-in-out infinite; }
  @keyframes girar { 0%, 20% { transform: rotate(0deg); } 60%, 100% { transform: rotate(-90deg); } }
  @media (prefers-reduced-motion: reduce) { .rotate svg { animation: none; transform: rotate(-90deg); } }
  @media (orientation: portrait) and (max-width: 900px) {
    body:not(.skip):not(.turned) .rotate { display: grid; }
    body:not(.skip):not(.turned) .scroller { display: none; }
  }
  @media (orientation: landscape) and (max-height: 520px) {
    .poster { padding-block: 26px 20px; gap: 18px; }
    .top h1 { font-size: clamp(1.7rem, 5vw, 2.4rem); }
    .grid { gap: 22px; }
  }

  .sheet {
    display: none; position: fixed; inset: 0; z-index: 200; background: rgba(10, 20, 22, .65);
    align-items: center; justify-content: center;
    padding: max(10px, env(safe-area-inset-top, 0px)) max(12px, env(safe-area-inset-right, 0px)) max(10px, env(safe-area-inset-bottom, 0px)) max(12px, env(safe-area-inset-left, 0px));
  }
  .sheet.open { display: flex; }
  .panel {
    width: min(620px, 100%); max-height: 100%; overflow: auto; background: var(--panel); color: var(--fg);
    border: 4px solid var(--frame); border-radius: 16px; padding: 16px 18px 18px; display: grid; gap: 10px;
  }
  .panel header { display: grid; grid-template-columns: auto 1fr auto; gap: 12px; align-items: center; }
  .panel .big {
    font-family: var(--font-display); font-weight: 700; font-size: 1.6rem; line-height: 1;
    background: var(--teal); color: var(--on-teal); width: 44px; height: 44px; border-radius: 50%;
    display: grid; place-items: center;
  }
  .panel h2 { font-size: 1.35rem; color: var(--violet); text-transform: uppercase; }
  .panel textarea {
    width: 100%; font: inherit; color: var(--fg); background: var(--surface);
    border: 2px solid var(--line); border-radius: 10px; padding: 10px 12px; resize: vertical; min-height: 92px;
  }
  .panel textarea:focus-visible { outline: 3px solid var(--yellow); outline-offset: 2px; }
  .panel .row { display: flex; flex-wrap: wrap; gap: 10px; }
  .partial { font-style: italic; color: var(--muted); font-size: 15px; min-height: 1.2em; }
  .status { min-height: 1.4em; font-weight: 600; }
  .status.ok { background: #d6f3e8; color: #0d4a3f; padding: 6px 10px; border-radius: 8px; }
  .status.err { background: #fde2df; color: #7a1a12; padding: 6px 10px; border-radius: 8px; }
  .note { font-size: 14px; color: var(--muted); }
  .mic.listening { background: #e0453a; border-color: #e0453a; color: #fff; }
  .inbox { display: grid; gap: 10px; }
  .msgcard { background: var(--surface); border-radius: 10px; padding: 10px 12px; display: grid; gap: 4px; }
  .msghead { font-size: 13px; font-weight: 700; color: var(--muted); }
  .msgcard p { white-space: pre-wrap; overflow-wrap: anywhere; }
  .adminbar { max-width: 1060px; margin: 16px auto 0; display: flex; justify-content: center; }

  .stage { display: contents; }
  .turnbar { display: none; }
  @media (orientation: portrait) and (max-width: 900px) {
    body.turned { overflow: hidden; }
    body.turned .stage {
      display: block; position: fixed; top: 0; left: 0; overflow: hidden;
      width: 100vh; width: 100dvh; height: 100vw;
      transform-origin: 0 0; transform: rotate(90deg) translateY(-100%);
    }
    body.turned.flip .stage { transform: rotate(-90deg) translateX(-100%); }
    body.turned .scroller {
      position: absolute; inset: 0; overflow: auto; -webkit-overflow-scrolling: touch;
      padding: calc(14px + env(safe-area-inset-right, 0px)) calc(14px + env(safe-area-inset-bottom, 0px)) calc(20px + env(safe-area-inset-left, 0px)) calc(14px + env(safe-area-inset-top, 0px));
    }
    body.turned.flip .scroller {
      padding: calc(14px + env(safe-area-inset-left, 0px)) calc(14px + env(safe-area-inset-top, 0px)) calc(20px + env(safe-area-inset-right, 0px)) calc(14px + env(safe-area-inset-bottom, 0px));
    }
    body.turned .turnbar { display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; margin: 0 auto 12px; }
    body.turned .grid { grid-template-columns: 1.1fr 1fr; }
    body.turned .arrow { display: block; }
    body.turned .idea { grid-template-columns: 34px 1fr auto; }
    body.turned .idea .go { grid-column: auto; }
    body.turned .poster { padding-block: 26px 20px; gap: 18px; }
    body.turned .top h1 { font-size: 2.4rem; }
    body.turned .top .sub { font-size: 1.15rem; }
    body.turned .why h2 { font-size: 1.5rem; }
    body.turned .closing { font-size: 1.9rem; }
  }
</style>
</head>
<body>

<div class="rotate">
  <svg viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><rect x="19" y="6" width="26" height="52" rx="5"/><path d="M28 51h8"/></svg>
  <h2>Turn your phone</h2>
  <p>Turn your phone sideways and tap "I turned it". The poster turns with it.</p>
  <button class="btn" type="button" id="turn">I turned my phone</button>
  <button class="btn alt" type="button" id="skip">Keep it upright</button>
</div>

<div class="stage"><div class="scroller">
<div class="turnbar">
  <button class="btn alt" type="button" id="flip">Flip to the other side</button>
  <button class="btn alt" type="button" id="unturn">Upright view</button>
</div>

<div class="frame">
  <main class="poster">
    <header class="top">
      <div class="tag">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M12 3l8 3v6c0 4.5-3.2 8-8 9-4.8-1-8-4.5-8-9V6l8-3z"/><path d="M8.5 12l2.5 2.5 4.5-5"/></svg>
        Safe Community <span>| Volunteer group</span>
      </div>
      <h1>Let's fight crime!</h1>
      <p class="sub">A safe community depends on all of us!</p>
    </header>

    <div class="grid">
      <section aria-labelledby="ideias">
        <h2 class="eyebrow" id="ideias">What can we do? Here are three ideas:</h2>
        <p class="hintline">Tap an idea to speak or write your message.</p>
        <ol class="ideas">
          <li><button class="idea" type="button" data-i="1"><span class="n">1</span><span><b>Report it:</b> tell the authorities about criminal activity.</span><span class="go">Speak or write</span></button></li>
          <li><button class="idea" type="button" data-i="2"><span class="n">2</span><span><b>Respect the law:</b> respect people and everyone's rights.</span><span class="go">Speak or write</span></button></li>
          <li><button class="idea" type="button" data-i="3"><span class="n">3</span><span><b>Help your community:</b> take part in awareness and violence-prevention campaigns.</span><span class="go">Speak or write</span></button></li>
        </ol>

        <figure class="mapfig" aria-label="Illustration of the neighborhood with the plaza highlighted">
          <div class="map">
            <svg viewBox="0 0 420 270" role="img" aria-label="Illustrated aerial view of a neighborhood with trees, streets and a red marker">
              <rect width="420" height="270" fill="#7fb36f"/>
              <g fill="#3f8f4a">
                <circle cx="30" cy="40" r="16"/><circle cx="62" cy="22" r="12"/><circle cx="50" cy="86" r="14"/><circle cx="20" cy="140" r="18"/>
                <circle cx="70" cy="200" r="15"/><circle cx="28" cy="236" r="13"/><circle cx="120" cy="250" r="14"/><circle cx="170" cy="30" r="13"/>
                <circle cx="215" cy="22" r="11"/><circle cx="380" cy="30" r="16"/><circle cx="400" cy="90" r="13"/><circle cx="392" cy="170" r="17"/>
                <circle cx="350" cy="250" r="14"/><circle cx="300" cy="256" r="11"/>
              </g>
              <g fill="#2f7a3d">
                <circle cx="46" cy="60" r="9"/><circle cx="100" cy="228" r="9"/><circle cx="198" cy="52" r="8"/><circle cx="372" cy="62" r="9"/><circle cx="410" cy="206" r="9"/>
              </g>
              <g transform="rotate(-16 210 135)">
                <g stroke="#8e9aa6" stroke-width="12" stroke-linecap="butt">
                  <path d="M-40 130 H470"/><path d="M130 -40 V310"/><path d="M300 -40 V310"/>
                </g>
                <g stroke="#f4f4f0" stroke-width="1.5" stroke-dasharray="8 8" opacity=".8">
                  <path d="M-40 130 H470"/><path d="M130 -40 V310"/><path d="M300 -40 V310"/>
                </g>
                <g fill="#dfe6ee">
                  <rect x="150" y="30" width="62" height="38" rx="3"/><rect x="222" y="30" width="62" height="38" rx="3"/>
                  <rect x="150" y="76" width="62" height="38" rx="3"/><rect x="222" y="76" width="62" height="38" rx="3"/>
                  <rect x="320" y="30" width="60" height="38" rx="3"/><rect x="320" y="76" width="60" height="38" rx="3"/>
                  <rect x="150" y="146" width="62" height="40" rx="3"/><rect x="222" y="146" width="62" height="40" rx="3"/>
                  <rect x="320" y="146" width="60" height="40" rx="3"/><rect x="320" y="196" width="60" height="40" rx="3"/>
                  <rect x="60" y="30" width="56" height="38" rx="3"/><rect x="60" y="76" width="56" height="38" rx="3"/>
                  <rect x="150" y="196" width="62" height="40" rx="3"/>
                </g>
                <g fill="#3c6fb5">
                  <rect x="158" y="38" width="20" height="10"/><rect x="230" y="84" width="20" height="10"/><rect x="328" y="38" width="20" height="10"/>
                  <rect x="158" y="154" width="20" height="10"/><rect x="330" y="204" width="20" height="10"/>
                </g>
              </g>
              <path d="M250 112c-14 0-24 10-24 24 0 18 24 40 24 40s24-22 24-40c0-14-10-24-24-24z" fill="#e0453a"/>
              <circle cx="250" cy="136" r="9" fill="#fff"/>
              <path d="M262 190 Q292 238 338 236" fill="none" stroke="#e0453a" stroke-width="8" stroke-linecap="round"/>
              <path d="M330 220 L352 238 L328 252 Z" fill="#e0453a"/>
            </svg>
          </div>
          <figcaption class="maplabel">Our neighborhood</figcaption>
          <div class="zoom">
            <svg viewBox="0 0 200 200" role="img" aria-label="Plaza with people gathered">
              <rect width="200" height="200" fill="#67b05a"/>
              <circle cx="100" cy="100" r="48" fill="none" stroke="#e3d3ac" stroke-width="12"/>
              <circle cx="100" cy="100" r="22" fill="#9ec8e8"/>
              <circle cx="100" cy="100" r="9" fill="#dff0fb"/>
              <g fill="#3d8445"><circle cx="22" cy="30" r="20"/><circle cx="178" cy="26" r="22"/><circle cx="170" cy="176" r="22"/><circle cx="26" cy="170" r="20"/></g>
              <g>
                <circle cx="52" cy="70" r="6" fill="#2f6fd6"/><circle cx="62" cy="130" r="6" fill="#e0453a"/><circle cx="148" cy="64" r="6" fill="#2f6fd6"/>
                <circle cx="150" cy="138" r="6" fill="#f2b705"/><circle cx="100" cy="164" r="6" fill="#2f6fd6"/><circle cx="104" cy="38" r="6" fill="#e0453a"/>
                <circle cx="40" cy="100" r="6" fill="#fff"/><circle cx="162" cy="100" r="6" fill="#fff"/>
              </g>
            </svg>
          </div>
          <div class="zoomlabel">Community plaza</div>
        </figure>
      </section>

      <div class="right">
        <aside class="event" aria-label="Next community event">
          <svg class="arrow" viewBox="0 0 54 54" fill="none" stroke="currentColor" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M6 8 C 30 4, 44 20, 40 44"/><path d="M28 36 L40 46 L48 30"/></svg>
          <div class="label">Next community event</div>
          <div>Community plaza</div>
          <div>Saturday, November 28</div>
          <div>9 a.m.–12 p.m.</div>
          <span class="chip">Example: replace with real details</span>
        </aside>

        <section class="why" aria-labelledby="prejuizo">
          <h2 id="prejuizo">How does crime harm society?</h2>
          <div class="photo">
            <svg viewBox="0 0 360 190" role="img" aria-label="Three smiling volunteers in blue shirts">
              <rect width="360" height="190" fill="#4f9a54"/>
              <g fill="#3d8445"><circle cx="30" cy="40" r="34"/><circle cx="330" cy="30" r="38"/><circle cx="180" cy="20" r="30"/></g>
              <g transform="translate(90 0)">
                <path d="M-36 190 v-52 a36 36 0 0 1 36 -36 a36 36 0 0 1 36 36 v52z" fill="#2f6fd6"/>
                <circle cy="72" r="26" fill="#f1c9a5"/><path d="M-27 68 a27 27 0 0 1 54 0 q-27 -16 -54 0z" fill="#3a2a20"/>
                <path d="M0 118 l13 5 v11 c0 8 -6 14 -13 17 c-7 -3 -13 -9 -13 -17 v-11z" fill="#fff" opacity=".9"/>
              </g>
              <g transform="translate(180 8)">
                <path d="M-36 182 v-52 a36 36 0 0 1 36 -36 a36 36 0 0 1 36 36 v52z" fill="#2f6fd6"/>
                <circle cy="64" r="26" fill="#8a5a3c"/><path d="M-27 60 a27 27 0 0 1 54 0 q-27 -14 -54 0z" fill="#1d1612"/>
                <path d="M0 110 l13 5 v11 c0 8 -6 14 -13 17 c-7 -3 -13 -9 -13 -17 v-11z" fill="#fff" opacity=".9"/>
              </g>
              <g transform="translate(270 0)">
                <path d="M-36 190 v-52 a36 36 0 0 1 36 -36 a36 36 0 0 1 36 36 v52z" fill="#2f6fd6"/>
                <circle cy="72" r="26" fill="#d9a67a"/><path d="M-27 68 a27 27 0 0 1 54 0 q-27 -16 -54 0z" fill="#7a4a24"/>
                <path d="M0 118 l13 5 v11 c0 8 -6 14 -13 17 c-7 -3 -13 -9 -13 -17 v-11z" fill="#fff" opacity=".9"/>
              </g>
              <g fill="#1d1612"><circle cx="82" cy="74" r="2.4"/><circle cx="98" cy="74" r="2.4"/><circle cx="172" cy="66" r="2.4"/><circle cx="188" cy="66" r="2.4"/><circle cx="262" cy="74" r="2.4"/><circle cx="278" cy="74" r="2.4"/></g>
              <g fill="none" stroke="#1d1612" stroke-width="2" stroke-linecap="round"><path d="M84 83 q6 5 12 0"/><path d="M174 75 q6 5 12 0"/><path d="M264 83 q6 5 12 0"/></g>
            </svg>
          </div>
          <p>Crime causes fear and insecurity and harms family life.</p>
          <ul>
            <li>It holds back the development of communities.</li>
            <li>It affects how people live together.</li>
          </ul>
        </section>

        <p class="message">Safety is everyone's responsibility. With respect, courtesy and unity, we can build a better place to live!</p>
      </div>
    </div>

    <h2 class="closing">Together for a safer community!</h2>

    <footer class="contact">
      <p><strong>Emergency (Brazil):</strong> call 190 (Military Police). <strong>Anonymous tips:</strong> Disque Denúncia 181, available in several states.</p>
      <p>For more information, add your group's website or phone number here.</p>
    </footer>
  </main>
</div>

<div class="adminbar"><button class="btn alt" type="button" id="open-inbox" hidden>View received messages</button></div>
</div>

<div class="sheet" id="sheet" role="dialog" aria-modal="true" aria-labelledby="sheet-title">
  <div class="panel">
    <header>
      <span class="big" id="sheet-n">1</span>
      <h2 id="sheet-title"></h2>
      <button class="btn alt" type="button" id="sheet-close">Close</button>
    </header>
    <p id="sheet-prompt"></p>
    <label class="sr" for="msg">Your message</label>
    <textarea id="msg" rows="4" maxlength="1500"></textarea>
    <p class="partial" id="partial" aria-live="polite"></p>
    <div class="row">
      <button class="btn alt mic" type="button" id="mic" hidden>
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><rect x="9" y="3" width="6" height="12" rx="3"/><path d="M5 11a7 7 0 0 0 14 0M12 18v3"/></svg>
        <span id="mic-label">Speak</span>
      </button>
      <button class="btn" type="button" id="send" hidden>Send to the group</button>
      <a class="btn alt" id="wa" target="_blank" rel="noopener noreferrer" href="#">Send via WhatsApp</a>
      <button class="btn alt" type="button" id="copy">Copy</button>
    </div>
    <p class="status" id="status" role="status"></p>
    <p class="note" id="note"></p>
    <p class="note" id="hint" hidden>Tip: to speak, tap the microphone on your phone's keyboard.</p>
  </div>
</div>

<div class="sheet" id="inbox" role="dialog" aria-modal="true" aria-label="Received messages">
  <div class="panel">
    <header>
      <span></span>
      <h2>Received messages</h2>
      <button class="btn alt" type="button" id="inbox-close">Close</button>
    </header>
    <div class="row"><button class="btn alt" type="button" id="inbox-refresh">Refresh</button></div>
    <div class="inbox" id="inbox-list"></div>
  </div>
</div>
</div>

<script>
(function () {
  var IDEAS = {
    1: {
      titulo: "Report it", tipo: "Report",
      prompt: "Tell us what happened, where and when. Do not accuse anyone by name without proof.",
      placeholder: "E.g., last night, on such-and-such street, I saw...",
      nota: "This message does not go to the police. In danger, call 190. Anonymous tips: Disque Denúncia 181, available in several Brazilian states."
    },
    2: {
      titulo: "Respect the law", tipo: "Pledge",
      prompt: "Write your pledge to the community.",
      placeholder: "I pledge to respect people, shared spaces and the law...",
      nota: "Even a small pledge helps: respect people and everyone's rights."
    },
    3: {
      titulo: "Help your community", tipo: "Idea",
      prompt: "How do you want to help? It could be a clean-up day, a school talk, a community conversation or a social media campaign.",
      placeholder: "I can help with...",
      nota: "Take part in awareness and violence-prevention campaigns."
    }
  };

  var $ = function (id) { return document.getElementById(id); };
  var sheet = $("sheet"), msg = $("msg"), statusEl = $("status"), sendBtn = $("send"),
      waLink = $("wa"), micBtn = $("mic"), micLabel = $("mic-label"), partialEl = $("partial"),
      noteEl = $("note"), hintEl = $("hint"), inboxEl = $("inbox"), inboxList = $("inbox-list"),
      openInbox = $("open-inbox");
  var current = 0, drafts = {}, lastFocus = null;
  var user = null, db = null, dict = null, uid = null, canSend = false;

  function setStatus(text, kind) {
    statusEl.textContent = text || "";
    statusEl.className = "status" + (kind ? " " + kind : "");
  }
  function hasText() { return msg.value.trim().length > 0; }
  function refresh() {
    var ok = hasText();
    waLink.setAttribute("aria-disabled", ok ? "false" : "true");
    waLink.href = ok ? "https://wa.me/?text=" + encodeURIComponent("Safe Community (" + IDEAS[current].titulo + "): " + msg.value.trim()) : "#";
    sendBtn.disabled = !ok;
  }

  function openSheet(n) {
    var idea = IDEAS[n];
    current = n;
    lastFocus = document.activeElement;
    $("sheet-n").textContent = String(n);
    $("sheet-title").textContent = idea.titulo;
    $("sheet-prompt").textContent = idea.prompt;
    msg.placeholder = idea.placeholder;
    msg.value = drafts[n] || "";
    noteEl.textContent = idea.nota + (canSend ? " When you send to the group, whoever manages this page can see your name." : "");
    partialEl.textContent = "";
    setStatus("");
    refresh();
    sheet.classList.add("open");
    msg.focus();
  }
  function closeSheet() {
    if (dict && dict.active()) { dict.stop().catch(function () {}); }
    drafts[current] = msg.value;
    sheet.classList.remove("open");
    if (lastFocus && lastFocus.focus) { lastFocus.focus(); }
  }

  Array.prototype.forEach.call(document.querySelectorAll(".idea"), function (b) {
    b.addEventListener("click", function () { openSheet(Number(b.getAttribute("data-i"))); });
  });
  $("sheet-close").addEventListener("click", closeSheet);
  sheet.addEventListener("click", function (e) { if (e.target === sheet) { closeSheet(); } });
  inboxEl.addEventListener("click", function (e) { if (e.target === inboxEl) { inboxEl.classList.remove("open"); } });
  document.addEventListener("keydown", function (e) {
    if (e.key === "Escape") {
      if (sheet.classList.contains("open")) { closeSheet(); }
      inboxEl.classList.remove("open");
    }
  });
  $("skip").addEventListener("click", function () { document.body.classList.add("skip"); });
  $("turn").addEventListener("click", function () { document.body.classList.add("turned"); });
  $("flip").addEventListener("click", function () { document.body.classList.toggle("flip"); });
  $("unturn").addEventListener("click", function () {
    document.body.classList.remove("turned");
    document.body.classList.add("skip");
  });
  msg.addEventListener("input", function () { drafts[current] = msg.value; refresh(); });

  waLink.addEventListener("click", function (e) {
    if (!hasText()) { e.preventDefault(); setStatus("Write or say something before sending.", "err"); }
  });

  $("copy").addEventListener("click", function () {
    if (!hasText()) { setStatus("Write or say something before copying.", "err"); return; }
    var text = msg.value.trim();
    var done = function () { setStatus("Text copied.", "ok"); };
    var fail = function () { msg.focus(); msg.select(); setStatus("Couldn't copy automatically. The text is selected: copy it from your phone's menu.", "err"); };
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(done, fail);
    } else { fail(); }
  });

  function sendError(e) {
    var c = e && e.code;
    if (c === "invalid_argument") { return "Your access doesn't allow sending to the group. Use WhatsApp, or ask whoever shared the page to let you contribute."; }
    if (c === "quota_exceeded") { return "The message box is full. Use WhatsApp."; }
    return "Couldn't send right now. Try again or use WhatsApp.";
  }

  sendBtn.addEventListener("click", async function () {
    var text = msg.value.trim();
    if (!text || !db || !uid) { return; }
    sendBtn.disabled = true;
    setStatus("Sending...");
    try {
      var ref = db.doc("mensagens/" + uid);
      var snap = await ref.get();
      var old = snap.exists && snap.data() && Array.isArray(snap.data().itens) ? snap.data().itens : [];
      var itens = old.slice();
      itens.unshift({ id: String(Date.now()), tipo: IDEAS[current].tipo, texto: text, em: new Date().toISOString() });
      if (itens.length > 100) { itens.length = 100; }
      await ref.set({ itens: itens });
      msg.value = "";
      drafts[current] = "";
      setStatus("Message sent to the group. Thank you!", "ok");
    } catch (e) {
      setStatus(sendError(e), "err");
    }
    refresh();
  });

  function renderInbox(rows, profs) {
    inboxList.textContent = "";
    if (!rows.length) {
      var p = document.createElement("p");
      p.textContent = "No messages yet.";
      inboxList.appendChild(p);
      return;
    }
    rows.forEach(function (r) {
      var card = document.createElement("article");
      card.className = "msgcard";
      var head = document.createElement("div");
      head.className = "msghead";
      var who = (profs[r.uid] && profs[r.uid].name) || "Someone";
      var when = r.it.em ? new Date(r.it.em).toLocaleString("en-US") : "";
      head.textContent = who + " · " + (r.it.tipo || "") + " · " + when;
      var body = document.createElement("p");
      body.textContent = r.it.texto || "";
      card.appendChild(head);
      card.appendChild(body);
      inboxList.appendChild(card);
    });
  }
  async function loadInbox() {
    inboxList.textContent = "Loading...";
    try {
      var snap = await db.collection("mensagens").get();
      var rows = [], ids = [];
      snap.docs.forEach(function (d) {
        var data = d.data() || {};
        ids.push(d.id);
        (Array.isArray(data.itens) ? data.itens : []).forEach(function (it) { rows.push({ uid: d.id, it: it }); });
      });
      rows.sort(function (a, b) { return String(b.it.em || "").localeCompare(String(a.it.em || "")); });
      var profs = user && ids.length ? await user.profiles(ids) : {};
      renderInbox(rows, profs);
    } catch (e) {
      inboxList.textContent = "Couldn't load the messages right now.";
    }
  }
  openInbox.addEventListener("click", function () { inboxEl.classList.add("open"); loadInbox(); });
  $("inbox-close").addEventListener("click", function () { inboxEl.classList.remove("open"); });
  $("inbox-refresh").addEventListener("click", loadInbox);

  function wireDictation() {
    micBtn.hidden = false;
    hintEl.hidden = true;
    dict.onPartial(function (e) { partialEl.textContent = e.text || ""; });
    dict.onFinal(function (e) {
      var t = e.text || "";
      if (!msg.value) { t = t.replace(/^\s+/, ""); }
      msg.value += t;
      drafts[current] = msg.value;
      partialEl.textContent = "";
      refresh();
    });
    dict.onState(function (e) {
      var on = e.state !== "idle";
      micBtn.classList.toggle("listening", on);
      micLabel.textContent = on ? "Stop" : "Speak";
      if (e.state === "idle" && e.reason === "not_granted") { setStatus("Microphone access wasn't allowed. You can type instead.", "err"); }
      if (e.state === "idle" && e.reason === "unavailable") { micBtn.hidden = true; hintEl.hidden = false; }
    });
    micBtn.addEventListener("click", function () {
      if (dict.active()) { dict.stop().catch(function () {}); return; }
      dict.start().catch(function (err) {
        var c = err && err.code;
        if (c === "not_granted") { setStatus("Microphone access wasn't allowed. You can type instead.", "err"); }
        else if (c === "unavailable") { micBtn.hidden = true; hintEl.hidden = false; }
        else if (c !== "dismissed" && c !== "stopped") { setStatus("Couldn't listen right now. You can type instead.", "err"); }
      });
    });
  }

  hintEl.hidden = false;
  (async function init() {
    var c = window.claude;
    if (!c || !c.use) { return; }
    var got = await Promise.all([
      c.use("user").catch(function () { return null; }),
      c.use("db").catch(function () { return null; }),
      c.use("dictation").catch(function () { return null; })
    ]);
    user = got[0]; db = got[1]; dict = got[2];
    if (user) {
      uid = await user.id();
      var w = await user.can("data.write");
      canSend = !!(db && uid && w !== false);
      if (db && (await user.canEdit())) { openInbox.hidden = false; }
    }
    if (canSend) { sendBtn.hidden = false; }
    if (dict) { wireDictation(); }
  })();
})();
</script>
</body>
</html>
