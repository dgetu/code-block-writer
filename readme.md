code-block-writer
=================

[![Build Status](https://travis-ci.org/dsherret/code-block-writer.svg)](https://travis-ci.org/dsherret/code-block-writer)
[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)

A simple code writer that assists with formatting and visualizing blocks of code.

## Example

```typescript
import CodeBlockWriter from "code-block-writer";

const writer = new CodeBlockWriter({ newLine: "\r\n" }); // optional options (newLine defaults to "\n")
const className = "MyClass";

writer.write(`class ${className} extends OtherClass`).block(() => {
    writer.writeLine(`@MyDecorator("myArgument1", "myArgument2")`);
    writer.write(`myMethod(myParam: any)`).block(() => {
        writer.write(`return this.post("myArgument");`);
    });
});

console.log(writer.toString());
```

Outputs:

```text
class MyClass extends OtherClass {
   @MyDecorator("myArgument1", "myArgument2")
   myMethod(myParam: any) {
       return this.post("myArgument");
   }
}
```