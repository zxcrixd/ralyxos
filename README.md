# RalyxOS

RalyxOS is a Debian-based Linux distribution using the Linux kernel, GRUB, XFCE, and Debian's official APT repositories. It provides an installer ISO, not a live system.

## Optional AI integration

The target system includes an optional `ralyx-ai` terminal helper for Groq's OpenAI-compatible API. **Never put an API key in this repository, an ISO, a workflow, or shell history.** Configure it after installation using a newly generated key:

```sh
export GROQ_API_KEY='your-new-key'
ralyx-ai 'Explain how to check Wi-Fi drivers on Debian'
```

For persistence, use a protected file such as `~/.config/ralyxos/ai.env` with mode 600 and source it from your shell profile. `GROQ_MODEL` can override the default model. Prompts are sent to Groq; do not send passwords, private keys, or sensitive personal data. Network access and Groq account limits/pricing apply.

## Important security note

The API key previously pasted in chat is considered compromised because it was exposed in plain text. Revoke it immediately in the Groq dashboard and create a replacement. It has not been added to the repository or build workflow.

## Build status

The current GitHub Actions workflow is still a Debian netinst test baseline, not a genuinely customized RalyxOS installer. The RalyxOS package and branding files are prepared, but the installer-image generation must be switched to a Debian Installer build before the result should be called a finished RalyxOS ISO.
