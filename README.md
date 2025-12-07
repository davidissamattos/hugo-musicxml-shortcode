# Hugo MusicXML Shortcode

This shortcode renders a MusicXML score with OpenSheetMusicDisplay. It supports a compact preview, a toggleable full score, and optional metadata pulled from the shortcode parameters.

## Parameters

All boolean-like parameters treat `false`, `0`, `no`, or `off` (case-insensitive) as `false`. Any other value is treated as `true`.

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `file` | string | – | Path to the MusicXML file to load. Required unless inline content is provided inside the shortcode. |
| `title` | string | `"View full score"` | Title shown above the metadata panel and used for the Flat.io link. |
| `preview` | bool | `true` | Enables the small preview excerpt inside the `<summary>`. |
| `previewMeasures` | number | `4` | Number of measures to show in the preview excerpt (still clamped by `toMeasure`). |
| `fold` | bool | `true` | Wraps the viewer in a `<details>` so the score can be collapsed. |
| `flat` | bool | `true` | Shows the "Add to Flat" link when a `file` is provided. |
| `hideTitle` | bool | `false` | Hides the score title in the full OSMD rendering. |
| `hideComposer` | bool | `false` | Hides composer and lyricist labels in both preview and full renderings. |
| `hidePartName` | bool | `false` | Hides the part/staff labels on the score. |
| `part` | string or comma-separated list | all parts | Limits rendering to specific parts. Match by part name or MusicXML part ID. Example: `part="Solo Cornet,Horn"` |
| `fromMeasure` | number | `1` | First measure to draw in both preview and full score. |
| `toMeasure` | number | last measure | Final measure to draw. Omit or set `< 1` to show the complete score. |

Any additional parameters are displayed in the metadata list under the score heading (unless explicitly hidden inside the shortcode template).

## Example

```go-html-template
{{< musicxml
      title="Solo feature"
      file="/musicxml/arban/10-first-studies/arban_first_studies_01.musicxml"
      previewMeasures="6"
      hideComposer="true"
      part="Cornet"
      fromMeasure="5"
      toMeasure="20"
>}}
{{< /musicxml >}}
```

This example renders only the Cornet part, starts at measure 5, stops at measure 20, hides the composer credit, and shows a six-measure preview.
