# ~tilde-hashtag

Extract tilde (~tilde) and/or hashtags (#hashtag) from any text

## How to use

```javascript
const extract = require('tildemention-hashtag')

const tildes = extract('Any text with ~tilde');
// ~tildes == ['~tilde']

const hashtags = extract('Any text with #hashtag', '#');
// hashtags == ['#hashtag']

const all = extract('Any text with #hashtag and ~tilde and ~othertilde', 'all');
// all == { ~tildes: ['~tilde', '@other~tilde'], hashtags: ['#hashtag'] }
```

NOTE: The extract of tilde is by default. For extract hashtags, the '#' symbol in second parameter is required.

## Options

### Exclude repeated tokens

```javascript
const tilde = extract('Any text with ~tilde and ~tilde and @othertilde', { unique: true });
// ~tildes == ['~tilde', '@other~tilde']

const hashtags = extract('Any text with #hashtag and #hashtag and #otherhashtag', { unique: true, type: '#' });
// hashtags == ['#hashtag', '#otherhashtag']

const all = extract('Any text with #hashtag and #hashtag and ~tilde and ~tilde', { unique: true, type: 'all' });
// all == { ~tildes: ['~tilde'], hashtags: ['#hashtag'] }
```

NOTE: The symbol '#' is communicated in 'type' property of second parameter

### Remove '@' and '#' symbols

```javascript
const tilde = extract('Any text with ~tilde and ~othertilde', { symbol: false });
// ~tildes == ['~tilde', 'other~tilde']

const hashtags = extract('Any text with #hashtag and #otherhashtag', { symbol: false, type: '#' });
// hashtags == ['hashtag', 'otherhashtag']

const all = extract('Any text with #hashtag and ~tilde', { symbol: false, type: 'all' });
// all == { ~tildes: ['tilde'], hashtags: ['hashtag'] }
```

## Mix

### Unique, symbol and type properties are mixables

```javascript
const ~tildes = extract('Any text with ~tilde and ~tilde and ~othertilde', { symbol: false, unique: true });
// ~tildes == ['~tilde', '~othertilde']

const hashtags = extract('Any text with #hashtag and #hashtag and #otherhashtag', { symbol: false, unique: true, type: '#' });
// hashtags == ['hashtag', 'otherhashtag']

const all = extract('Any text with #hashtag and #hashtag and ~tilde and ~tilde', { symbol: false, unique: true, type: 'all' });
// all == { ~tildes: ['~tilde'], hashtags: ['hashtag'] }
```

## Run test

```
$ npm install && npm test
```

## License

MIT © [realprinceviper](https://github.com/realprinceviper)
