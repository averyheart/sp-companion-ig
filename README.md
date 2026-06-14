# sp-instagram

Character Instagram profile pages for the Saucepan AI companion platform. Each character has a self-contained profile page styled after Instagram, fetching content dynamically from this repository.

## Structure

```
sp-instagram/
├── index.html                  # Landing page listing all characters
├── shared/
│   └── boot.js                 # Shared React component—all characters use this
├── avatars/                    # Commenter profile pictures (filename = username with periods replaced by underscores)
└── characters/
    └── luca/
        ├── index.html          # Luca's profile entry point
        ├── posts.json          # Profile data, posts, highlights, and comments
        └── images/             # Character images and GIFs
```

## Adding a New Post

1. Upload the image or GIF to `characters/<name>/images/`
2. Add a new entry at the top of the `posts` array in `characters/<name>/posts.json`

```json
{
  "id": 2,
  "src": "filename.jpg",
  "caption": "Caption text.",
  "location": "Location name or null",
  "likes": 10000,
  "commentCount": 84,
  "date": "1d",
  "comments": [
    { "user": "@username", "text": "Comment text." }
  ]
}
```

## Adding a New Character

1. Create `characters/<name>/` with `index.html`, `posts.json`, and `images/`
2. Copy `characters/luca/index.html`—no changes needed, the character is detected from the URL path automatically
3. Add a link to the root `index.html`

## Adding Commenter Avatars

Upload images to the `avatars/` folder at the root. Filenames are derived from the commenter's username: remove the `@`, and replace any periods with underscores.

| Username | Filename |
|----------|----------|
| `@kai.fc` | `kai_fc.jpg` |
| `@nordic_football` | `nordic_football.jpg` |
| `@london.terrace` | `london_terrace.jpg` |

If no avatar image is found, the component falls back to an initials placeholder automatically.

## posts.json Profile Fields

| Field | Description |
|-------|-------------|
| `name` | Display name |
| `username` | Handle including `@` |
| `avatar` | Filename in `images/` |
| `companion_id` | Saucepan companion ID—the string after `/companion/` in the URL |
| `bio` | Profile bio text |
| `verified` | Boolean |
| `followers` | Display string, e.g. `"2.4M"` |
| `following` | Number |

## Highlights Template

```json
"highlights": [
  {
    "id": "h1",
    "label": "Matchday",
    "cover": "matchday-cover.jpg",
    "images": [
      "matchday-01.jpg",
      "matchday-02.jpg",
      "matchday-03.jpg"
    ]
  }
]
```

## Live URLs

| Page | URL |
|------|-----|
| Character list | `https://sp-instagram.vercel.app/` |
| Luca Bergren | `https://sp-instagram.vercel.app/characters/luca/` |
