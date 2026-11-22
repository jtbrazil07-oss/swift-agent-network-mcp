# Swift Agent Network MCP server

A read-only MCP server for the [Swift Agent Network](https://swiftagentnetwork.com/) member directory: licensed and registered local businesses in the United States, each matched to a state license file or the FMCSA register. Members include real estate agents, insurance agents, moving companies, bus and limo operators and contractors.

The network lists members. It does not rate or rank them, send messages or make bookings.

**Endpoint:** `https://swiftagentnetwork.com/mcp` (Streamable HTTP, no sign-in, no API key)

## Tools

| Tool | What it does | Arguments |
|---|---|---|
| `search_members` | Find members by state, city, line of work or name. Each result links the member's page and the city and state pages that list everyone there. | `state`, `city`, `line`, `name`, `limit` |
| `get_member` | One member by slug, with their next open time when they take bookings. | `slug` |
| `how_to_contact` | The public ways to reach a member: directory page, own website, phone if shown. | `slug` |
| `open_times` | Times a member has free in the next 1 to 7 days, with the link where the person books it themselves. | `slug`, `days` |

## Connect

Claude Desktop, Claude Code, Cursor and other MCP clients can add it as a remote server:

```json
{
  "mcpServers": {
    "swift-agent-network": {
      "type": "http",
      "url": "https://swiftagentnetwork.com/mcp"
    }
  }
}
```

Claude Code: `claude mcp add --transport http swift-agent-network https://swiftagentnetwork.com/mcp`

## Where the data comes from

Every member is matched to a public record: a state license file (for example the Texas Real Estate Commission or the Colorado Division of Real Estate) or, for movers and bus companies, the FMCSA register. The member adds their own phone, photo and website. Each state page on [swiftagentnetwork.com](https://swiftagentnetwork.com/) names its source and the date it was copied.

## Listing in this repo

`server.json` is the listing for the [official MCP Registry](https://registry.modelcontextprotocol.io). The server itself runs on swiftagentnetwork.com; this repository holds only the listing and this page.

## License

The files in this repository (this page, `server.json` and `glama.json`) are under the [MIT License](LICENSE). The member directory the server returns is not: it is the network's data, served under the terms at [swiftagentnetwork.com](https://swiftagentnetwork.com/).

Questions: mail@swiftagentsites.com
