# Rhino Linux Wiki

This is the official Rhino Linux Wiki, built with [Nextra](https://nextra.site).

[**Live Demo →**](https://rhino-linux-wiki.vercel.app)

[![](https://github.com/user-attachments/assets/ae8f5395-34df-4352-84f0-0dea02dfd0ad)](https://rhino-linux-wiki.vercel.app)

## Quick Start

### Deploy with Vercel

Click the button to clone this repository and deploy it on Vercel:

[![](https://vercel.com/button)](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2Fshuding%2Fnextra-docs-template&showOptionalTeamCreation=false)

### Deploy without Vercel

Set the following repository secrets for GitHub Actions:
- generate an ssh keygen pair and set `SSH_USER`, `SSH_IP`, `SSH_DIR`, and `SSH_KEY`:
  - `SSH_USER` - the host user
  - `SSH_IP` - the IP of the server
  - `SSH_DIR` - the desired directory to copy to 
  - `SSH_KEY` - the contents of the generated `site_build_key` file:
```bash
# generate key
ssh-keygen -t ed25519 -C "github-actions@site-build" -f site_build_key < /dev/null

# allow key to login to user
mkdir -p ~/.ssh
cat site_build_key.pub >> ~/.ssh/authorized_keys

# print key result to set SSH_KEY - DO NOT SHARE!!
cat site_build_key
```

- The workflow will run:
  - On any changes to the `main` branch
  - Manually on dispatch
    - For security, it will always checkout from `main`, even if requesting dispatch on an alternate branch

## Local Development

First, run `pnpm i` to install the dependencies.

Then, run:
```bash
npx concurrently "pnpm dev" "npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch"
```
This will start the development server at `localhost:3000`, or if port `:3000` is taken up, the next accessible port (e.g. `:3001`).
This will also keep `tailwindcss` running while you work, so `div` entries in wiki pages and `input.css` changes are properly added.

## License

This project is licensed under the MIT License.
