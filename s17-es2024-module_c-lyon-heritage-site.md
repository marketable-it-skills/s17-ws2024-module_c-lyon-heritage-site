# Test Project Outline – Module C – Web Technologies

#### Competition time

3 hours

## Introduction

Welcome to Lyon. This vibrant city is known for its historical significance and architectural beauty. In this project, editors have written articles introducing notable heritage sites in Lyon, France. Each article is created in `.html` or `.txt` format, with front-matter embedded for metadata. Files are stored in the `content-pages` folder, which may contain nested subfolders.

You are tasked with creating a website to host these articles, maintaining the existing article workflow and structure.

## General Description of Project and Tasks

This project does not require a database. Content is managed through static files in the `content-pages` directory and its subfolders. Users should be able to access the home page listing all pages and sub-folders.

The website will list and load these static files. Files provided follow the format: `YYYY-MM-DD-title-in-lower-case-with-hyphens.html` or `.txt`.

Example filenames:

- `2024-09-01-example-page.html`
- `2024-10-20-greatest-lyon-heritage-site.html`
- `2025-01-01-a-post-for-future-posting.txt`

There is one central `images` folder under `content-pages`. All image paths mentioned in the articles are relative to this central images folder, regardless of their location within subfolders.

## Requirements

### URL Routes

Define URL routes for listing content, accessing pages, and querying tags:

#### Examples

- `/heritages/2024-09-01-example-page` shows the page for `2024-09-01-example-page.html` or `.txt`

- `/heritages/sub-folder-name` lists the pages and sub-folders inside `sub-folder-name`

- `/heritages/sub-folder-name/2024-09-10-welcome-to-lyon` shows the file inside `sub-folder-name`

- `/heritages/sub-folder-1/sub-folder-2/2024-09-10-welcome-to-lyon` works the same for nested folders

- `/`: Index listing.

- `/heritages/YYYY-MM-DD-title`: Displays content page.

- `/heritages/sub-folder-name`: Lists sub-folder contents.

- `/tags/tag-name`: Lists pages containing the specified tag.

### Content Listing

The list shows titles and summaries, linking to individual pages. Exclude:

- Pages dated in the future.
- Draft pages — that is, files where the `draft` key is set to `true` in the front-matter. If the `draft` key is missing or set to any value other than `true`, the page is not considered a draft.
- Pages without a valid date prefix (i.e., the first 11 characters not in `YYYY-MM-DD-` format).

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

HTML content renders directly. Text files render lines as paragraphs. Lines without spaces that end in a valid image extension (e.g. `.jpg`, `.png`) should be rendered as `<img>` tags.

### Image Handling

Cover images specified in front-matter or default to filenames in `images` folder. A radial gradient spotlight effect follows the cursor on cover images. In this project, we do not need to consider the possibility of a missing cover image. Image paths in both `.html` and `.txt` files must be transformed to match the final served path structure. In this project, we do not need to consider the possibility of a missing cover image.

### Page Elements

- **Title**: Determined using the following priority:

  1. If a `title` is defined in the front-matter, use it.
  2. If not, use the text content of the first `<h1>` element in the HTML content.
  3. If neither is available, derive it from the filename by removing the date and replacing hyphens with spaces, then capitalizing each word.

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
