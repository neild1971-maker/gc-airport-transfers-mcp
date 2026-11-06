# GC Airport Transfers MCP Server

Hosted remote [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) server for **GC Airport Transfers** — private (not shared-shuttle) airport and cruise transfers on the Gold Coast and Brisbane, Queensland, Australia (also Byron Bay / Northern Rivers NSW).

This repository is documentation only. There is no application source code here. The live server is operated by GC Airport Transfers.

## Remote endpoint

- **URL:** `https://gc-airporttransfers.com/wp-json/atb-gateway/v1/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** OAuth required (OAuth 2.1 with PKCE). Unauthenticated requests receive `401`.

## Official MCP Registry

- **Name:** `com.gc-airporttransfers/booking`
- **Registry search:** https://registry.modelcontextprotocol.io/v0.1/servers?search=com.gc-airporttransfers

## Tools

| Tool | Purpose |
| --- | --- |
| `get_service_info` | Fleet, policies, service area and contact details |
| `get_quote` | Exact fixed-price quote for a route (read-only) |
| `check_availability` | Whether a pick-up date and time can be booked (read-only) |
| `request_booking` | Lodges a booking request for the operator to confirm |

Payment is never taken through the MCP tools. The operator confirms every booking and the customer pays by an emailed link.

## Website and docs

- Website: https://gc-airporttransfers.com.au
- AI / MCP gateway docs: https://gc-airporttransfers.com.au/ai-agent-gateway/

## Client configuration (remote)

Example for an MCP client that supports a remote Streamable HTTP server with OAuth:

```json
{
  "mcpServers": {
    "gc-airport-transfers": {
      "url": "https://gc-airporttransfers.com/wp-json/atb-gateway/v1/mcp"
    }
  }
}
```

Connect with an OAuth-capable MCP client. The server returns `401` with a `resource_metadata` pointer until the client completes OAuth.

## License

MIT (this documentation repository). The hosted MCP service itself is a proprietary commercial service operated by GC Airport Transfers.
