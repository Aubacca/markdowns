# Regular Expression

Check that first character is a vowel and last character is equal to first character:

```javascript
/^(a|e|i|o|u).*\1$/.test("abdasdfasdfasdfasdfasdfadsfadasfa");
```

Explanation:

- /^ : check at the beginning.
- (a|e|i|o|u) : must be one of those voweles and remembers the match. These are called capturing groups.
- .\* : anything can be defined here.
- \1$ : check that the last character is the same as the first character
