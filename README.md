# Terminal Commands API

A JSON API of **100 useful terminal commands** for **Windows**, **Mac**, and **Linux**.

## Data shape

Each command has:

| Field     | Type   | Description                    |
|----------|--------|--------------------------------|
| `id`     | number | Unique identifier (1–100)      |
| `command`| string | The terminal command           |
| `desc`   | string | Short description              |
| `os`     | string | Target OS: `win`, `mac`, `linux` (comma-separated if multiple) |

## Using as an API

After you push this repo to GitHub, you can use the **raw JSON** as an API.

### Get all commands

**Raw URL (replace `USER` and `REPO` with your GitHub username and repo name):**

```
https://raw.githubusercontent.com/USER/REPO/main/commands.json
```

Example with `fetch` (browser or Node):

```js
const res = await fetch('https://raw.githubusercontent.com/USER/REPO/main/commands.json');
const data = await res.json();
console.log(data.commands); // array of 100 commands
```

### Filter by OS (client-side)

```js
const winCommands = data.commands.filter(c => c.os.includes('win'));
const macCommands = data.commands.filter(c => c.os.includes('mac'));
const linuxCommands = data.commands.filter(c => c.os.includes('linux'));
```

### Get by ID

```js
const cmd = data.commands.find(c => c.id === 42);
```

## Files

- **`commands.json`** – All 100 commands. Root object has a `commands` array.

## License

Use as you like.
