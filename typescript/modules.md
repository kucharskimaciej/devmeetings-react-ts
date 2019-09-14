# Modules

Both modern JS and TypeScript support modules. Each file is a module, than can export some properties:

```typescript
// src/foo.ts
export const foo = 12
```

Which then are imported in another file:

```typescript
// src/bar.ts
import { foo } from "./foo"
```

Each file can also have a default export, which means you don't have to name the exported property:

```typescript
// src/baz.ts
export default 42;
```

You can name it when importing:

```typescript
// src/bar.ts
import Baz from "./baz";
```

You can also mix both styles:

```typescript
import DefaultExport, { namedExport1, namedExport2 } from "./a-file"
```

## Importing npm modules

Importing code installed via npm is done by specifying the package name instead of relative path:

```typescript
import React from "react"
```

Some (usually older) packages have no default export and have to be imported as a group of properties;

```typescript
import * as _ from "underscore"
```


### Resources

- [Modules](https://www.typescriptlang.org/docs/handbook/modules.html)
- [`export default` considered harmful](https://basarat.gitbooks.io/typescript/docs/tips/defaultIsBad.html)
