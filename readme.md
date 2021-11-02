# Javascript

## Jest

### Generates a Jest it.each table block
**Name**: iteach

#### Generates

> it.each\` <br/>
>    note &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| given     | expected <br/>
>    ${'should'}                                                            | ${{}} &nbsp;&nbsp;| ${{}} <br/>
>    ${'should'}                                                            | ${{}} &nbsp;&nbsp;| ${{}} <br/>
>   \`('$note given: $given expected: $expected ', async ({given, expected}) => { <br/>
>    <br/>
> }); <br/>

#### Template

```
<template name="iteach" value="it.each`&#10;   note           | $NAME1$     | $NAME2$               &#10;   ${'should'}    | ${$VALUE1$} | ${$VALUE2$}&#10;   ${'should'}    | ${$VALUE1$} | ${$VALUE2$}&#10;  `('$note $NAME1$: $$$NAME1$ $NAME2$: $$$NAME2$ ', async ({$NAME1$, $NAME2$}) =&gt; {&#10;  $END$&#10;});" description="generates it each block" toReformat="false" toShortenFQNames="true">
  <variable name="NAME1" expression="&quot;given&quot;" defaultValue="" alwaysStopAt="true" />
  <variable name="VALUE1" expression="&quot;{}&quot;" defaultValue="" alwaysStopAt="true" />
  <variable name="NAME2" expression="&quot;expected&quot;" defaultValue="" alwaysStopAt="true" />
  <variable name="VALUE2" expression="&quot;{}&quot;" defaultValue="" alwaysStopAt="true" />
  <context>
    <option name="JS_STATEMENT" value="true" />
  </context>
</template>
```

### Creates a Jest mock from selected string
**Name**: jmck
 
#### Generates
**From (if selected)**
> '../src/example/path.ts'

**To**

> jest.mock('../src/example/path.ts', () => ({
>   __esModule: true,
>   default: jest.fn()
> }));

#### Template

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
