# Sticker shirt gallery

A free GitHub Pages site for the QR code on the shirt.

- `index.html` is the public gallery people see after scanning: every GIF and sticker in a scrollable grid. Tap one to open it big, swipe between them, and save or share it.
- `admin.html` is your private editor: upload new GIFs and stickers, drag to reorder, rename the page title, delete.
- `gallery.json` holds the list and order. The admin page edits it for you.
- `gifs/` is where uploads land (created on the first upload).

## Setup (about 10 minutes, one time)

1. Create a **public** repository on GitHub, for example `stickers`, and upload these files to it.
2. In the repo go to **Settings → Pages**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
   After a minute your site is live at `https://<username>.github.io/stickers/`.
3. Make an access token for the admin page:
   GitHub **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
   - Repository access: **Only select repositories** → your `stickers` repo
   - Permissions → Repository permissions → **Contents: Read and write**
   - Pick an expiration you're comfortable with
4. Open `https://<username>.github.io/stickers/admin.html`. The first time, it shows **One-time setup**:
   fill in the token and pick an admin password (10+ characters, a short phrase works well), then tap **Save password**.
5. That's it. From now on admin.html shows just a password box.

## Sharing admin with someone else

Send them two things: the link `https://<username>.github.io/stickers/admin.html` and the password.
They type the password once, leave "Keep me signed in on this phone" ticked, and they're in.
They never see GitHub or the token.

To change the password (or lock someone out), sign in, tap **Change password**, and set a new one.
People already signed in on their phone stay signed in until they tap **Sign out**, so to fully lock someone out,
also delete the token on GitHub and run setup again with a new token.

### How the password works

The token is stored in the repo as `admin-key.json`, encrypted with your password (AES-256, with a slow key derivation that makes guessing expensive).
The repo is public, so a weak password could be brute-forced offline. Use a phrase of a few words, not a short word.
Even in the worst case, the token can only edit this one sticker repo.

## Using the admin page

- **Add**: tap **+ Add GIFs or stickers** and pick files. They upload right away, then tap **Save**.
- **Reorder**: hold the ≡ handle and drag (or use ↑), then **Save**.
- **Delete**: tap Delete, then **Save**.
- The public page updates about a minute after saving (GitHub rebuilds the site).

## WhatsApp stickers

WhatsApp stickers are `.webp` files, and animated ones play in phone browsers as is.
Easiest way to get them out: forward the sticker to yourself on WhatsApp Web, then right-click → Save image.
Keep each file under ~5 MB so the page loads fast on mobile data.

## The QR code

Point the QR at `https://<username>.github.io/stickers/`, never at a specific file.
You can then add stickers forever without reprinting the shirt.
Use error correction level **H** and print it at least 6–8 cm wide.
