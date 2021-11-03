# Awesome Intellij Live Templates

> A curated list of awesome Intellij Live Templates
- [Javascript](#javascript)
  - [Jest](#jest)
    - [Generates a Jest `it.each` table block](#generates-a-jest-iteach-table-block)
    - [Creates a `jest.mock` from selected string](#creates-a-jestmock-from-selected-string)
 - [Java](#java)
    - [Spring](#spring)
      - [Create a Spring Bean with a list of dependencies](#create-a-spring-bean-with-a-list-of-dependencies)
    - [JUnit](#junit)
      - [Generate a JUnit5 unit test](#create-a-spring-bean-with-a-list-of-dependencies)
    - [Hamcrest](#hamcrest)
      - [Generate a Hamcrest `is` assert and static import matchers](generate-a-hamcrest-`is`-assert-and-static-import-matchers)

## Javascript

### Jest

#### Generates a Jest `it.each` table block
**Name**: iteach

##### Generates

```javascript
it.each`
  note          | given  | expected
  ${'should'}   | ${{}}  | ${{}}
  ${'should'}   | ${{}}  | ${{}}
  `('$note given: $given expected: $expected ', async ({given, expected}) => {
  
  }); 
```
##### Template

```xml
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

#### Creates a `jest.mock` from selected string
**Name**: jmck
 
##### Generates
**From (if selected)**
```
'../src/example/path.ts'
```
**To**

```javascript
jest.mock('../src/example/path.ts', () => ({
  __esModule: true,
  default: jest.fn()
}));
```

##### Template

```xml
<template name="jmck" value="jest.mock($SELECTION$, () =&gt; ({&#10;  __esModule: true,&#10;  $END$default: jest.fn()&#10;}));" description="add a mock stub" toReformat="false" toShortenFQNames="true">
  <context>
    <option name="JAVA_SCRIPT" value="true" />
    <option name="JSX_HTML" value="false" />
    <option name="JS_CLASS" value="false" />
    <option name="JS_EXPRESSION" value="false" />
  </context>
</template>
```

## Java

### Spring

#### Create a Spring Bean with a list of dependencies

**Name**: BEAN

##### Generates

```java
@Bean
$CLASS_NAME$ $beanName$($PARAMETERS$) {
    return new $CLASS_NAME$($parametersToPass$);
}
```

##### Template

```xml
<template name="BEAN" value="@org.springframework.context.annotation.Bean&#10;$CLASS_NAME$ $beanName$($PARAMETERS$) {&#10;    return new $CLASS_NAME$($parametersToPass$);&#10;}" description="Create a default Bean for a class." toReformat="true" toShortenFQNames="true" useStaticImport="true">
  <variable name="CLASS_NAME" expression="" defaultValue="" alwaysStopAt="true" />
  <variable name="beanName" expression="camelCase(CLASS_NAME)" defaultValue="" alwaysStopAt="false" />
  <variable name="PARAMETERS" expression="" defaultValue="" alwaysStopAt="true" />
  <variable name="parametersToPass" expression="regularExpression(PARAMETERS, &quot;(^|,\\s*)\\S+\\s+&quot;, &quot;$1&quot;)" defaultValue="" alwaysStopAt="false" />
  <context>
    <option name="JAVA_DECLARATION" value="true" />
  </context>
</template>
```

### JUnit

#### Generate a JUnit5 unit test

**Name**: TEST

##### Generates

```java
@Test
@DisplayName("$TEST_TITLE$")
void $TEST_NAME$() {
    $END$
}
```

##### Template

```
<template name="TEST" value="@org.junit.jupiter.api.Test&#10;@org.junit.jupiter.api.DisplayName(&quot;$TEST_TITLE$&quot;)&#10;void $TEST_NAME$() {&#10;    $END$&#10;}" description="Create a standard JUnit5 test." toReformat="false" toShortenFQNames="true">
  <variable name="TEST_TITLE" expression="" defaultValue="" alwaysStopAt="true" />
  <variable name="TEST_NAME" expression="" defaultValue="" alwaysStopAt="true" />
  <context>
    <option name="JAVA_DECLARATION" value="true" />
  </context>
</template>
```

### Hamcrest

#### Generate a Hamcrest `is` assert and static import matchers

**Name**: ASSIS

##### Generates

```java
assertThat($expression$, is($expected$));
```

##### Template

```xml
<template name="ASSIS" value="org.hamcrest.MatcherAssert.assertThat($expression$, org.hamcrest.Matchers.is($expected$));" description="Hamcrest assertThat(x, is())" toReformat="false" toShortenFQNames="true" useStaticImport="true">
  <variable name="expression" expression="" defaultValue="" alwaysStopAt="true" />
  <variable name="expected" expression="" defaultValue="" alwaysStopAt="true" />
  <context>
    <option name="JAVA_EXPRESSION" value="true" />
    <option name="JAVA_STATEMENT" value="true" />
  </context>
</template>
```
