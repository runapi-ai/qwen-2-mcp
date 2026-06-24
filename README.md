# @runapi.ai/qwen-2-mcp

RunAPI MCP server for the **Qwen 2** model line. Create tasks,
poll their status, and check pricing through a single RunAPI API key.

## Tools

- `edit_image` — create a Qwen 2 task (edit image) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `qwen-2-edit-image`, `qwen-2-remix-image`, `qwen-2-text-to-image`.
- `remix_image` — create a Qwen 2 task (remix image) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `qwen-2-edit-image`, `qwen-2-remix-image`, `qwen-2-text-to-image`.
- `text_to_image` — create a Qwen 2 task (text to image) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `qwen-2-edit-image`, `qwen-2-remix-image`, `qwen-2-text-to-image`.
- `get_task` — fetch the current status and latest payload for a task.
- `check_pricing` — look up pricing for a model in this line.

## Configuration

Set a RunAPI API key via the `RUNAPI_API_KEY` environment variable, or write
it to `~/.config/runapi/config.json`:

```bash
mkdir -p ~/.config/runapi
echo '{"api_key":"YOUR_KEY"}' > ~/.config/runapi/config.json
```

Get an API key at https://runapi.ai. Pricing is listed at
https://runapi.ai/pricing.

## Usage

Run the server over stdio:

```bash
npx -y @runapi.ai/qwen-2-mcp
```

Add it to an MCP client (see `examples/` for per-client configs):

```json
{
  "mcpServers": {
    "qwen-2": {
      "command": "npx",
      "args": ["-y", "@runapi.ai/qwen-2-mcp"],
      "env": { "RUNAPI_API_KEY": "${RUNAPI_API_KEY}" }
    }
  }
}
```

## License

Apache-2.0
