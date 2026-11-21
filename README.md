# RalyxOS

RalyxOS is a Debian-based Linux distribution using the Linux kernel, GRUB, XFCE, and Debian's official APT repositories. It provides an installer ISO, not a live system.

## AI integration

RalyxOS includes an optional `ralyx-ai` terminal helper for Groq's OpenAI-compatible API. **The API key must never be placed in this repository, the ISO, a workflow file, or shell history.** Configure it locally after installation:

```sh
export GROQ_API_KEY='your-new-key'
ralyx-ai 'Explain how to check Wi-Fi drivers on Debian'
```

For persistence, use a protected file such as `~/.config/ralyxos/ai.env` with mode 600 and source it from your shell profile. Do not commit that file. `GROQ_MODEL` can override the default model.

The helper sends the prompt to Groq. Do not send passwords, private keys, personal data, or other sensitive information. Network access is required, and Groq's terms, limits, and pricing apply.

## Build

The current GitHub Actions workflow produces a Debian Bookworm amd64 netinst installer as a test baseline. It is **not yet a genuinely customized RalyxOS ISO**; the next build step is to generate a Debian installer image with RalyxOS packages, branding, and preseed configuration rather than renaming the upstream ISO.

## Security

Never publish API keys. If a key is exposed, revoke it immediately at the provider dashboard and create a replacement. Hardware support and the optional AI service depend on Debian, network access, and the target device.
