# HAPP - split routing for AI services

The URL of `ai-only-routing.json` is **not an HAPP import URL**. It is a source file only. Do not paste the raw JSON GitHub URL into HAPP; that can produce a parsing error.

## Import

1. Open [the HAPP deeplink text file](https://raw.githubusercontent.com/albert22531/open_sourse/main/happ/ai-only-routing.deeplink.txt).
2. **Copy its entire content**. It begins with `happ://routing/onadd/`. Copy the content, not the browser address bar URL.
3. In HAPP > Routing / Routing profiles, import from clipboard. Or open the copied deeplink on the device with HAPP installed.
4. Select the new profile, enable routing and reconnect the VPN session. HAPP downloads GeoIP/GeoSite files on initial import.

Rules: `GlobalProxy=false`; 106 explicit AI service domains and `geosite:category-ai-!cn` use VPN; everything else goes DIRECT. Do not use `domain:com` or `domain:ai` unless you truly intend ALL websites on those TLDs to use VPN.

If importing profiles is disabled for a provider-managed **JSON subscription**, HAPP documentation says its routing profiles are exclusively controlled by the subscription provider; use an ordinary editable server list/subscription instead.

Source JSON: [ai-only-routing.json](./ai-only-routing.json).
Official HAPP documentation: https://www.happ.su/main/dev-docs/routing
