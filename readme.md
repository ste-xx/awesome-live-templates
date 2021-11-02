
### Creates a Jest mock from selected string
**Name**: jmck

**Language:** js/ts
 
### Example
**From (if selected)**
> '../src/example/path.ts'

**To**

> jest.mock('../src/example/path.ts', () => ({
>   __esModule: true,
>   default: jest.fn()
> }));

```
<template name="jmck" value="jest.mock($SELECTION$, () =&gt; ({&#10;  __esModule: true,&#10;  $END$default: jest.fn()&#10;}));" description="add a mock stub" toReformat="false" toShortenFQNames="true">
  <context>
    <option name="JAVA_SCRIPT" value="true" />
    <option name="JSX_HTML" value="false" />
    <option name="JS_CLASS" value="false" />
    <option name="JS_EXPRESSION" value="false" />
  </context>
</template>
```
