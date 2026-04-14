# Caption Files Structure

## Overview

Captions are now split by language for better maintainability and performance. The app only downloads the language file it needs.

## Files Created

### Index File
- **captions_index.json** - Lists all available languages and their file names

### Language Files (Ready to upload)
- **captions_en.json** - English captions (Complete ✅)
- **captions_hi.json** - Hindi captions (Complete ✅)
- **captions_bn.json** - Bengali captions (Template - needs translation)
- **captions_te.json** - Telugu captions (Template - needs translation)
- **captions_mr.json** - Marathi captions (Template - needs translation)
- **captions_ta.json** - Tamil captions (Template - needs translation)
- **captions_gu.json** - Gujarati captions (Template - needs translation)
- **captions_kn.json** - Kannada captions (Template - needs translation)

## How It Works

1. App starts and fetches `captions_index.json`
2. Based on user's language preference, app fetches the specific language file (e.g., `captions_hi.json`)
3. App uses captions from that language file
4. If language file fails to load, app falls back to English

## Benefits

✅ **Smaller downloads** - Only download the language user needs (~15KB vs ~120KB)  
✅ **Easy updates** - Update one language without affecting others  
✅ **Add languages easily** - Just add new language file and update index  
✅ **Better organization** - Each translator can work on their own file  
✅ **Version control** - Track changes per language independently

## File Structure

Each language file contains:
```json
{
  "version": "1.0.0",
  "language": "hi",
  "language_name": "हिंदी",
  "last_updated": "2026-04-13",
  "captions": {
    "good_morning_general": [...],
    "good_morning_spiritual": [...],
    "good_afternoon": [...],
    // ... all categories
  }
}
```

## Upload to GitHub

1. Upload all `captions_*.json` files to your GitHub repository root
2. Upload `captions_index.json` to repository root
3. Update `base_url` in captions_index.json with your GitHub details
4. Test URL: `https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main/captions_en.json`

## Adding New Language

1. Copy `captions_en.json` to `captions_XX.json` (XX = language code)
2. Update `language` and `language_name` fields
3. Translate all caption texts
4. Add new language entry to `captions_index.json`
5. Commit to GitHub

## Translation Guidelines

- Keep format consistent: `"Quote"\nGreeting!`
- For 30 good morning captions, create 30 unique quotes
- For festivals, maintain cultural relevance
- For spiritual captions, use single word greeting
- Test special characters display correctly

## Current Status

| Language | File | Status | Notes |
|----------|------|--------|-------|
| English | captions_en.json | ✅ Complete | 30 unique quotes |
| Hindi | captions_hi.json | ✅ Complete | 30 translated quotes |
| Bengali | captions_bn.json | 📝 Template | Needs translation |
| Telugu | captions_te.json | 📝 Template | Needs translation |
| Marathi | captions_mr.json | 📝 Template | Needs translation |
| Tamil | captions_ta.json | 📝 Template | Needs translation |
| Gujarati | captions_gu.json | 📝 Template | Needs translation |
| Kannada | captions_kn.json | 📝 Template | Needs translation |

## Maintenance

**To update captions:**
1. Edit the specific language file on GitHub
2. Click "Commit changes"
3. App will fetch updated captions on next launch

**To add new category:**
1. Add category with captions in English file
2. Translate and add to other language files
3. Update app code to use new category

**Version management:**
- Increment `version` field when making changes
- App can check version to determine if cache needs refresh
- Update `last_updated` date with each change
