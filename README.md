# UTC Explorer

A live analog clock for learning how Eastern time and UTC relate. The green hands show Eastern time, and a red hand shows UTC. Drag the red hand to move through the day and watch the green hands follow, then press a button to jump back to the current time.

It is a single HTML file with no dependencies.

## What it shows

- **Green hour and minute hands:** current Eastern time (`America/New_York`). Daylight saving is handled automatically, so the label reads EDT or EST as appropriate.
- **Red hand:** the UTC hour on the same 12-hour dial. The smaller gray-green numbers inside the dial (13 to 24) let you read it as 24-hour UTC.
- **Readouts:** digital time and date for both zones, plus how many hours UTC is ahead of Eastern. Dragging across midnight shows the two zones landing on different dates.
- **Everything moves in whole minutes.** There is no second hand.

## Using it

- **Drag** the red hand, ideally by the dashed ring at its tip. The Eastern hands keep the correct offset.
- **Keyboard:** focus the red hand and use the arrow keys (5 minutes) or Page Up / Page Down (1 hour).
- **Back to current time:** the button returns to live time. The label beside it shows LIVE or EXPLORING.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The standalone page. Open it in a browser, host it anywhere, or serve it with GitHub Pages. |
| `wordpress-embed.html` | The same clock as a paste-in snippet (`<style>`, a `<div>` and a `<script>`), with every style and name scoped under `.ucn` so it will not affect the host page. |

## Adding it to a website

**Standalone or iframe:** upload `index.html` to your host, for example as `/clock/index.html`, then link to it or embed it:

```html
<iframe src="/clock/" style="width:100%;height:900px;border:0"></iframe>
```

**WordPress:** add a Custom HTML block (not the Classic or Paragraph block), paste in the contents of `wordpress-embed.html`, and publish. Script tags are stripped for non-Administrator roles, so this needs an Administrator account.

## How it works

Plain HTML, CSS and vanilla JavaScript. The dial is an SVG drawn by the script, and Eastern time comes from the browser's built-in `Intl.DateTimeFormat`. Dragging uses pointer events (mouse, touch and pen), rotating the hand by however far the pointer turns around the center.

Fonts (Barlow Semi Condensed and IBM Plex Mono) are loaded from Google Fonts. Remove the `<link>` tag to fall back to system fonts.

Colors: black background, `#04650D` for the face, numbers and Eastern hands, `#E5232B` for the UTC hand.
