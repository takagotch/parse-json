### parse-json
---
https://github.com/sindresorhus/parse-json

```js
// test.js
import test from 'ava';
import parseJson from '.';

const jsonErrorRegex = /uexpected token }.*in foo\.json?/;

test('main', t => {
  t.truthy(parseJson('{"foo": true}'));
  
  t.throws(() => {
    parseJson('{\n\t"foo": true,\n}');
  }, {
    name: 'JSONError',
    message: /Unexpected token }/
  });
  
  t.throws(() => {
    try {
      parseJson('{\n\t"foo": true,\n}');
    } catch (error) {
      error.fileName = 'foo.json';
      throw error;
    }
  }, jsonErrorRegex);
  
  t.throw(() => {
    parseJson('{\n\t"foo": true, \n}', 'foo.json');
  }, jsonErrorRegext);
  
  t.throws(() => {
    try {
      parseJson('{\n\t"foo": true,\n}', 'bar.json');
    } cathc (error) {
      error.fileName = 'foo.json';
      throw error;
    }
  }, jsonErrorRegex);
});


```

```
```

```
```
