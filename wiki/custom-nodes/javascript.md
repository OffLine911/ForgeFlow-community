# JavaScript Nodes

Execute custom JavaScript code for data transformation and logic.

## How It Works

```javascript
// Access inputs via: input.fieldName
// Access previous output via: input._previousOutput
// Return value becomes the output

return transformedData;
```

## Available Globals

For security, only these are available:

| Global | Description |
|--------|-------------|
| `JSON` | Parse/stringify |
| `Math` | Math operations |
| `Date` | Date handling |
| `String` | String methods |
| `Number` | Number methods |
| `Boolean` | Boolean methods |
| `Array` | Array methods |
| `Object` | Object methods |
| `parseInt` | Parse integer |
| `parseFloat` | Parse float |
| `isNaN` | Check NaN |
| `isFinite` | Check finite |
| `encodeURIComponent` | URL encode |
| `decodeURIComponent` | URL decode |

## Examples

### Transform Data

```javascript
const data = input._previousOutput;

const result = data.map(item => ({
  name: item.name.toUpperCase(),
  value: item.value * 2
}));

return result;
```

---

### Filter Array

```javascript
const items = input._previousOutput;
const minValue = parseInt(input.min_value) || 0;

return items.filter(item => item.value > minValue);
```

---

### Sort Data

```javascript
const items = input._previousOutput;

return items.sort((a, b) => b.value - a.value);
```

---

### Generate Report

```javascript
const data = input._previousOutput;

return {
  generated: new Date().toISOString(),
  count: data.length,
  stats: {
    min: Math.min(...data.map(d => d.value)),
    max: Math.max(...data.map(d => d.value)),
    avg: data.reduce((a, b) => a + b.value, 0) / data.length
  }
};
```

---

### Parse & Extract

```javascript
const text = input._previousOutput;
const regex = new RegExp(input.pattern, 'g');
const matches = text.match(regex);

return {
  matches: matches || [],
  count: matches ? matches.length : 0
};
```

---

### Format String

```javascript
const template = input.template;
const data = input._previousOutput;

let result = template;
for (const [key, value] of Object.entries(data)) {
  result = result.replace(`{${key}}`, value);
}

return result;
```

---

### Merge Objects

```javascript
const obj1 = input._previousOutput;
const obj2 = JSON.parse(input.extra_data || '{}');

return { ...obj1, ...obj2 };
```

## Input Access

| Variable | Description |
|----------|-------------|
| `input.fieldName` | Your defined input fields |
| `input._previousOutput` | Previous node's output |

## Tips

- Always return a value
- Use try/catch for error handling
- Test complex logic separately first
- Keep scripts focused and simple
