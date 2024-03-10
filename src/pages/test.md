```javascript
// The ASCII characters we can use in our password are represented by char codes 32-126,
// and the sextets we want are in the range 26-51
const asciiCodes = [32..127];
const permittedBits = new Set([26..52].map(i => i.toBinary(wordLength=6)));
// Using this we can recursively generate all the passwords that encode to the wanted format
const generateStrings = (currentString, targetLength) => {
  if (targetLength <= 0) { return [currentString]; }
  return getAllowedCodes(currentString)
    .flatMap(code => {
      const candidateStr = currentString + char(code);
      // abort if it doesn't encode correctly
      const binary = candidateStr.toBinary(wordLength=8);
      for (let i = 0; i + 6 < binary.length; i += 6) {
        if (!permittedBits.has(binary[i..i+6])) { return []; }
      }
      // otherwise dive into this branch
      return generateStrings(candidateStr, targetLength - 1)
    });
};
```