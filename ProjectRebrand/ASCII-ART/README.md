# ASCII-ART

An experiment in rendering randomized ASCII dragon artwork as JPEG images.
The C# console application combines text templates, element colors, rarity,
and loot images using Magick.NET.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).

## Status

This is an experimental source project, not a packaged ASCII-art editor or a
general image-to-text converter. There is no published setup guide or verified
cross-platform workflow. The project targets **.NET 7** and references
`Magick.NET-Q16-HDRI-x64` version **13.0.0**.

## What the source does

- Selects dragon templates and colors using randomized element and rarity values.
- Draws text with a hardcoded `Consolas` font and composites loot PNG assets.
- Writes `output.jpg` and seed-named JPEG files into the output directory.

## Inspect and build

Clone the source and inspect `Program.cs` and the project file before running it:

```bash
git clone https://github.com/wispdevon/ASCII-ART.git
cd ASCII-ART
dotnet build "ASCII ART.csproj"
```

The build command is derived from the project file and has not been executed
as part of this documentation draft. Runtime code uses Windows-style paths,
expects the asset/output directories, and assumes a particular font. Resolve
those paths and dependencies in a development environment before trying:

```bash
dotnet run --project "ASCII ART.csproj"
```

The repository includes generated output and build directories. Their presence
does not establish a reproducible build on a fresh checkout.

## Contributing

Possible improvements are portable path handling, documented font and asset
requirements, an output-directory option, and a reproducible setup.
Open an [issue](https://github.com/wispdevon/ASCII-ART/issues) with the proposal
before expanding the experiment. Use generated examples rather than private images.

## License and assets

No license file is present. Reuse rights for the code, fonts, templates, and loot
images have not been established by this draft. Dependencies retain their own terms.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).
