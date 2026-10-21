# UTC Explorer

A live analog clock for learning how UTC relates to the time in any time zone abbreviation. The green hands show the zone you choose (Eastern Time by default), and a red hand shows UTC. Drag the red hand to move through the day and watch the green hands follow, then click "Back to live" to return to the current time.

It is a single HTML file with no dependencies.

## What it shows

- **Green hour and minute hands:** the time in the selected time zone, Eastern Time (`ET (EST/EDT)`) by default. Entries that list two offsets (ET, CT, MT, PT and AET) follow daylight saving automatically, so the label reads EDT or EST as appropriate. Every other entry is a fixed offset, exactly as listed.
- **Red hand:** the UTC hour on the same 12-hour dial. The smaller gray-green numbers inside the dial (13 to 24) let you read it as 24-hour UTC.
- **Readouts:** digital time and date for both zones, plus how far UTC is ahead of or behind the selected zone. Half-hour and 45-minute offsets such as India and Nepal work too. Dragging across midnight shows the two zones landing on different dates.
- **Everything moves in whole minutes.** There is no second hand.

## Using it

- **Drag** the red hand, ideally by the dashed ring at its tip. The green hands keep the correct offset.
- **Keyboard:** after you click or drag the red hand, the arrow keys nudge it by 5 minutes, and Page Up / Page Down by 1 hour. You can also Tab to the hand and use the same keys.
- **Time zone:** the drop-down lists all 212 entries from Wikipedia's list of time zone abbreviations, west to east, each as `Abbr - Name - UTC offset`, for example `EDT - Eastern Daylight Time (North America) - UTC−04:00`. Abbreviations that mean more than one thing, such as CST or IST, appear once per meaning. Choosing a zone snaps the clock back to live time in that zone.
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

## Data

The time zone list comes from Wikipedia's [List of time zone abbreviations](https://en.wikipedia.org/wiki/List_of_time_zone_abbreviations), used under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Three over-long names were shortened for the drop-down (British Summer Time, Eastern Caribbean Time and HAEC). Wikipedia's list is not an official standard, so check anything important against an authoritative source.

## How it works

Plain HTML, CSS and vanilla JavaScript. The dial is an SVG drawn by the script, and time zones come from the built-in `Intl.DateTimeFormat` (only for the five rows that follow daylight saving; the rest are plain offsets). Dragging uses pointer events (mouse, touch and pen), rotating the hand by however far the pointer turns around the center.

Fonts (Barlow Semi Condensed and IBM Plex Mono) are loaded from Google Fonts. Remove the `<link>` tag to fall back to system fonts.

Colors: black background, `#04650D` for the face, numbers and selected-zone hands, `#E5232B` for the UTC hand.
