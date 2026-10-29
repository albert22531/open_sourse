# HAPP selective AI routing

This repository contains the HAPP routing source JSON and a separate **HAPP deeplink**.

**Import:** https://raw.githubusercontent.com/albert22531/open_sourse/main/happ/ai-only-routing.deeplink.txt

Copy the **contents of that file** (starting with `happ://routing/onadd/`), not its HTTP URL. Import via HAPP Routing from clipboard, or open the deeplink with HAPP. The GitHub JSON URL is not a valid HAPP routing-import URL.

The profile is named `AI-only - rest DIRECT`. Importing again with the same name replaces the previous version on the same server-list subscription. Reconnect the VPN after importing. Restart Codex if it was stuck in a reconnect loop.

## Traffic handling

- `GlobalProxy=false`: unmatched destinations stay DIRECT
- `ProxySites`: AI domains, category AI and OpenAI/Codex authentication dependencies go through VPN
- `FakeDNS=true`: Xray handles the DNS mapping for domain-based split routing
- `DomainStrategy=IPIfNonMatch`: matches domain rules before optional IP lookups
- `RouteOrder=proxy-direct-block`: explicit proxy rules checked before direct rules
- HAPP GeoIP/GeoSite data URLs still have to download successfully

The OpenAI dependency hosts `challenges.cloudflare.com`, `workos.com`, and `statsig.com` can be shared by non-AI sites; traffic to those hosts may also use VPN. All other destinations fall back to DIRECT. This is **not** a blanket proxy for every `.com` or `.ai` site.

Codex requires long-lived WSS on TCP 443 to `chatgpt.com`. A server or network that interrupts WebSockets can still cause reconnect loops even with correct routing.

This profile has been checked for JSON and Base64 integrity, **not end-to-end validated on a specific HAPP Mac installation**.

Official references:
- HAPP routing: https://www.happ.su/main/ru/dev-docs/routing
- OpenAI network allowlist and WSS: https://help.openai.com/en/articles/9247338-network-recommendations-for-chatgpt-errors-on-web-and-apps
