<p align="center"><img src="logo.png" alt="IndiaCos MCP server logo" width="120"></p>

# IndiaCos MCP Server: Indian company, LLP, GST, PAN and director data for AI agents

> Look up any Indian business by GSTIN, CIN, PAN or DIN, build filtered lead lists, and check court cases, from Claude, ChatGPT, Cursor or any MCP client.

**MCP endpoint:** `https://indiacos.com/mcp` · **Transport:** Streamable HTTP · **Tools:** 13 · **Website:** [indiacos.com](https://indiacos.com)

This repository is the public listing for the **hosted** IndiaCos MCP server: connection instructions, the registry manifest (`server.json`) and client config files. There is nothing to install or self-host; the server runs at the URL above.

## Connect in one step

Add this URL to any MCP client that supports remote servers:

```
https://indiacos.com/mcp
```

### Claude (claude.ai, Claude Desktop, Claude mobile)
Settings → Connectors → **Add custom connector** → paste the URL above → Connect.

### Claude Code
```bash
claude mcp add --transport http indiacos https://indiacos.com/mcp
```
With an API key instead of OAuth:
```bash
claude mcp add --transport http indiacos https://indiacos.com/mcp --header "Authorization: Bearer YOUR_KEY"
```

### ChatGPT
Settings → Apps & Connectors → Advanced → enable Developer mode → **Create** a connector → paste the URL above.

### Cursor, Windsurf, Cline and other JSON-config clients
```json
{
  "mcpServers": {
    "indiacos": {
      "url": "https://indiacos.com/mcp"
    }
  }
}
```

### VS Code (GitHub Copilot)
Add to `.vscode/mcp.json`:
```json
{
  "servers": {
    "indiacos": {
      "type": "http",
      "url": "https://indiacos.com/mcp"
    }
  }
}
```

### Gemini CLI
```bash
gemini extensions install https://github.com/rchtjn2-gif/indiacos-mcp-server
```

## Authentication
OAuth 2.1: sign in with your IndiaCos account when your client asks. Or send an API key as a header: `Authorization: Bearer YOUR_KEY` (one key works for the REST API and MCP).

## What data it covers
- **31.8 lakh companies and 5.2 lakh LLPs** from the Ministry of Corporate Affairs (MCA)
- **51.6 lakh GST registrations**, including proprietors and partnerships that never appear in MCA data
- **PAN to every GSTIN** across states, **directors by DIN** with MCA disqualification-list checks
- **Court cases** naming a business, with cheque-bounce (s.138), fraud, insolvency and recovery flags
- **71 plain-language business categories** mapped from 3,969 NIC codes, filterable by state, district, pincode and dates
- Contact details (email, mobile) as filed, on keys with contact access; every read is logged

## Tools (13)
| Group | Tools |
|---|---|
| Search and lists | `search`,  find (plain-English, `e.g. 'solar EPC companies in Pune')` |
| Lookups | `get_gst`, `get_company`, `get_company_directors`, `get_pan`, `get_director`, `get_office` |
| Risk | `get_cases` |
| Contacts | get_contact (keys with contact access) |
| Wallet | `get_wallet`, `top_up_wallet`, `get_payment` |

## Example prompts
- "Verify GSTIN 27AAOCM9194L2ZF: legal name, status, directors and other GST registrations under the same PAN."
- "Find active pharma manufacturers in Gujarat incorporated after 2022."
- "Check this vendor for court cases, cheque-bounce flags and open charges before we extend credit."
- "List handicraft exporters in Jaipur with contact details."
- "Which companies share the registered office at this address?"

## Pricing
₹50 free credit on signup (about 312 calls), then ₹0.16 per successful call from a prepaid wallet. Errors and not-found answers are free. Top up ₹500, ₹5,000 or ₹50,000 (+18% GST) by UPI, card or net banking.

## FAQ
### Is there an MCP server for Indian company and GST data?
Yes. IndiaCos runs a hosted MCP server at https://indiacos.com/mcp with 3.7M companies and LLPs and 5.2M GST registrations, joined to directors, PAN and court records.

### Can my AI assistant verify a GSTIN or CIN?
Yes. Ask it to look up the GSTIN, CIN, PAN or DIN; it calls get_gst, get_company, get_pan or get_director and returns status, registered office, directors and linked registrations.

### Does it cover proprietorships, not just companies?
Yes. GST registrations cover proprietors, partnerships and branches that MCA-only data sources miss.

### How much does it cost?
₹50 free credit on signup, then ₹0.16 per successful call. No subscription.

### Where does the data come from?
Public government registers: MCA, GST, MCA disqualification lists and public court records.

## Links
- [API and MCP overview](https://indiacos.com/api)
- [API docs](https://indiacos.com/api/docs)
- [llms.txt](https://indiacos.com/llms.txt)
- [Server card](https://indiacos.com/.well-known/mcp.json)
- [Get an API key (₹50 free)](https://indiacos.com/signup)
- [Privacy policy](https://indiacos.com/privacy)
- [Terms and data licence](https://indiacos.com/terms)

## About this repository
This repo holds listing and configuration files only. The IndiaCos MCP server is a hosted service operated by IndiaCos; its use is governed by the terms linked above. The files in this repository are released under the MIT licence.
