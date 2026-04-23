# Bytes Matcher (ES)

[**⚖️** MIT](./LICENSE.md)

🔗
[GitHub](https://github.com/hugoalh/bytes-matcher-es)
[JSR](https://jsr.io/@hugoalh/bytes-matcher)
[NPM](https://www.npmjs.com/package/@hugoalh/bytes-matcher)

An ECMAScript module for bytes match.

## 🎯 Targets

| **Runtime \\ Source** | **GitHub Raw** | **JSR** | **NPM** |
|:--|:-:|:-:|:-:|
| **[Bun](https://bun.sh/)** >= v1.1.0 | ❌ | ✔️ | ✔️ |
| **[Deno](https://deno.land/)** >= v2.1.0 | ✔️ | ✔️ | ✔️ |
| **[NodeJS](https://nodejs.org/)** >= v20.9.0 | ❌ | ✔️ | ✔️ |

## 🛡️ Runtime Permissions

This does not request any runtime permission.

## #️⃣ Sources

- GitHub Raw
  ```
  https://raw.githubusercontent.com/hugoalh/bytes-matcher-es/{Tag}/mod.ts
  ```
- JSR
  ```
  jsr:@hugoalh/bytes-matcher[@{Tag}]
  ```
- NPM
  ```
  npm:@hugoalh/bytes-matcher[@{Tag}]
  ```

> [!NOTE]
> - It is recommended to include tag for immutability.
> - These are not part of the public APIs hence should not be used:
>   - Benchmark/Test file (e.g.: `example.bench.ts`, `example.test.ts`).
>   - Entrypoint name or path include any underscore prefix (e.g.: `_example.ts`, `foo/_example.ts`).
>   - Identifier/Namespace/Symbol include any underscore prefix (e.g.: `_example`, `Foo._example`).

## ⤵️ Entrypoints

| **Name** | **Path** | **Description** |
|:--|:--|:--|
| `.` | `./mod.ts` | Default. |

## 🧩 APIs

- ```ts
  class BytesMatcher {
    constructor(signature: BytesMatcherSignature<string | Uint8Array>[]);
    test(item: string | Uint8Array): boolean;
    testStream(file: string | URL | Deno.FsFile): Promise<boolean>;
    get weight(): number;
  }
  ```
- ```ts
  class MagicBytesMatcher {
    constructor(filter?: (meta: MagicBytesMeta) => boolean): this;
    match(item: string | Uint8Array): MagicBytesMetaExtend | null;
    matchAll(item: string | Uint8Array): Generator<MagicBytesMetaExtend>;
    matchFile(file: string | URL | Deno.FsFile): Promise<MagicBytesMetaExtend | null>;
    matchFileAll(file: string | URL | Deno.FsFile): AsyncGenerator<MagicBytesMetaExtend>;
    test(item: string | Uint8Array): boolean;
    testFile(file: string | URL | Deno.FsFile): Promise<boolean>;
  }
  ```
- ```ts
  interface BytesMatcherSignature<T extends string | Uint8Array> {
    offset: number;
    pattern: T;
  }
  ```
- ```ts
  interface MagicBytesMeta {
    category: MagicBytesMetaCategory;
    extensions: `.${string}`[];
    mimes: string[];
    name: string;
    variant?: string;
  }
  ```
- ```ts
  interface MagicBytesMetaExtend extends MagicBytesMeta {
    weight: number;
  }
  ```
- ```ts
  type MagicBytesMetaCategory = "archive" | "audio" | "compressed" | "database" | "diagram" | "disk" | "document" | "ebook" | "executable" | "font" | "formula" | "geospatial" | "image" | "metadata" | "model" | "other" | "package" | "playlist" | "presentation" | "rom" | "spreadsheet" | "subtitle" | "video";
  ```

> [!NOTE]
> - For the full or prettier documentation, can visit via:
>   - [Deno CLI `deno doc`](https://docs.deno.com/runtime/reference/cli/doc/)
>   - [JSR](https://jsr.io/@hugoalh/bytes-matcher)
