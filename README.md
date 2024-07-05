# fastexpr.js

A blazingly fast, single-file, zero dependency JavaScript expression parser.

## Features

- Fast. Hand-coded lexer and top-down operator precedence parser. Twice as fast as `esprima`.
- Small. Less than 10KB minified and gzipped.
- Compatible. Parses all valid JavaScript expressions. Produces an `esprima` style AST.

Usage:

```typescript
import {parse} from '@anpete/fastexpr';

const expr = (s: string) => `hello from ${s}!`;

const ast = parse(expr.toString());

console.log(ast);
```

which produces:

```typescript
{
  type: "ArrowFunctionExpression",
  params: [ { type: "IdentifierExpression", name: "s" } ],
  body: {
    type: "TemplateLiteralExpression",
    quasis: [
      {
        type: "TemplateExpression",
        value: { cooked: "hello from " },
        tail: false
      },
      {
        type: "TemplateExpression",
        value: { cooked: "!" },
        tail: true
      }
    ],
    expressions: [ { type: "IdentifierExpression", name: "s" } ]
  }
}
```
