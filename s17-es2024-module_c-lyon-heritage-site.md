# Test Project Outline – Module C – Web Technologies

#### Competition time

3 hours

## Introduction

Welcome to Lyon. This vibrant city is known for its historical significance and architectural beauty. In this project, editors have written articles introducing notable heritage sites in Lyon, France. Each article is created in `.html` or `.txt` format, with front-matter embedded for metadata. Files are stored in the `content-pages` folder, which may contain nested subfolders.

There is one central `images` folder under `content-pages`. All image paths mentioned in the articles are relative to this central images folder, regardless of their location within subfolders.

You are tasked with creating a website to host these articles, maintaining the existing article workflow and structure.

The website will list and load these static files, which follow the naming convention: `YYYY-MM-DD-title.txt` or `YYYY-MM-DD-title.html`.

The website will be accessible at `<http://wsXX.worldskills.org/XX_module_C/>`, where `XX` is your seat number.

## General Description of Project and Tasks

This project does not require a database. Content is managed through static files in the `content-pages` directory and its subfolders. Users should be able to access the home page listing all pages and sub-folders.

### Filename Convention

Files provided follow the format: `YYYY-MM-DD-title-in-lower-case-with-hyphens.html` or `.txt`.

Example filenames:

- `2024-09-01-example-page.html`
- `2024-10-20-greatest-lyon-heritage-site.html`
- `2025-01-01-a-post-for-future-posting.txt`

## Requirements

### URL Routes

Define URL routes for listing content, accessing pages, and querying tags:

- `/XX_module_c/`: Index listing.
- `/XX_module_c/heritages/YYYY-MM-DD-title`: Displays content page.
- `/XX_module_c/heritages/sub-folder-name`: Lists sub-folder contents.
- `/XX_module_c/tags/tag-name`: Lists pages containing the specified tag.

All paths are relative to `<http://wsXX.worldskills.org>`.

### Content Listing

The list shows titles and summaries, linking to individual pages. Exclude:

- Pages dated in the future.
- Draft pages (`draft: true` in front-matter).
- Pages without proper date format (`YYYY-MM-DD-`).

Sub-folders are listed alphabetically, followed by content pages in reversed alphabetical order (latest at top).

### Tags and Search

Implement tag filtering (`/tags/tag-name`) and a search input for page titles and content, supporting multiple keywords separated by `/`.

### Content Pages

Each content file includes:

- Optional front-matter (`---` delimited).
- Main content.

Example front-matter:

```
title: Example Page
tags: example, test
cover: example-cover.jpeg
summary: Sample summary.
```

HTML content renders directly. Text files render lines as paragraphs, and standalone image paths as `<img>` tags.

### Image Handling

Cover images specified in front-matter or default to filenames in `images` folder. A radial gradient spotlight effect follows the cursor on cover images.

### Page Elements

- **Title**: Derived from front-matter, `<h1>` tag, or filename.
- **Aside Information**: Date, tags, draft status (sticky on scroll).
- **Main Content**: Dynamically loaded.

Photos expand on click, reverting on second click or scroll. First paragraph has a drop cap spanning three lines.

### Accessibility and Meta Tags

Ensure accessibility compliance using the aXe tool. Define social sharing meta tags.

### GitHub and File Management

Provide a `.gitignore` to exclude `node_modules` and temporary folders.

## Assessment

Project evaluation will be conducted using Google Chrome and the aXe accessibility tool.

#### Mark distribution

| WSOS SECTION | Description       | Points |
| ------------ | ----------------- | ------ |
| 1            | Files and Listing | 7.0    |
| 2            | Search and Tags   | 2.0    |
| 3            | Loading files     | 5.5    |
| 4            | Layout            | 6.75   |
| **Total**    |                   | 21.25  |
