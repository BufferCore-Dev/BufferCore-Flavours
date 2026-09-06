# BufferCore Flavours

BufferCore Flavours are reusable primitive-value baselines that sit on top of BufferCore without changing its semantic architecture.

Each leaf Flavour is a folder containing `flavour.json`. Folder/category paths are organisational only and have no runtime meaning.

```text
BufferCore-Flavours/
└── flavours/
    └── <any organisational folders>/
        └── my-flavour/
            └── flavour.json
```

A Flavour contains primitive overrides only:

```json
{
  "schemaVersion": 1,
  "type": "buffercore-flavour",
  "id": "my-flavour",
  "displayName": "My Flavour",
  "overrides": {
    "--bc-color-identity-ramp-1": "#123456",
    "--bc-radius-md": "12px"
  }
}
```

Do not copy semantic values into a Flavour. Engine applies the primitive overrides and then re-resolves the existing BufferCore semantic alias graph.

Build the Core baseline:

```powershell
cd ..\BufferCore-Engine
npm run core:build
```

Build with a Flavour selected by id:

```powershell
npm run core:build -- --flavour my-flavour
```

A direct Flavour directory or `flavour.json` path can also be supplied to `--flavour`. The default Flavour repository is the sibling `BufferCore-Flavours` directory; use `--flavours-root <path>` only when needed.
