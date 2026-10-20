# UTC Explorer

A live analog clock for learning how UTC relates to the time in any time zone. The green hands show the zone you choose (Eastern by default), and a red hand shows UTC. Drag the red hand to move through the day and watch the green hands follow, then click "Back to live" to return to the current time.

It is a single HTML file with no dependencies.

## What it shows

- **Green hour and minute hands:** the time in the selected time zone, Eastern (`America/New_York`) by default. Daylight saving is handled automatically, so the label reads EDT or EST as appropriate.
- **Red hand:** the UTC hour on the same 12-hour dial. The smaller gray-green numbers inside the dial (13 to 24) let you read it as 24-hour UTC.
- **Readouts:** digital time and date for both zones, plus how far UTC is ahead of or behind the selected zone. Half-hour and 45-minute zones such as India and Nepal work too. Dragging across midnight shows the two zones landing on different dates.
- **Everything moves in whole minutes.** There is no second hand.

## Using it

- **Drag** the red hand, ideally by the dashed ring at its tip. The green hands keep the correct offset.
- **Keyboard:** focus the red hand and use the arrow keys (5 minutes) or Page Up / Page Down (1 hour).
- **Time zone:** the drop-down lists every zone your browser knows, with a short Common group at the top. Eastern is the default.
- **Back to live:** while you are exploring, a red "Back to live" link beside the drop-down returns to the current time. It reads LIVE when the clock is already live.

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

Plain HTML, CSS and vanilla JavaScript. The dial is an SVG drawn by the script, and time zone conversion comes from the browser's built-in `Intl.DateTimeFormat`. Dragging uses pointer events (mouse, touch and pen), rotating the hand by however far the pointer turns around the center.

Fonts (Barlow Semi Condensed and IBM Plex Mono) are loaded from Google Fonts. Remove the `<link>` tag to fall back to system fonts.

Colors: black background, `#04650D` for the face, numbers and selected-zone hands, `#E5232B` for the UTC hand.
