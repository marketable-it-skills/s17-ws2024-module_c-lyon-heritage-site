# Test Project Outline – Module C – Lyon Heritage Sites

#### Competition time

3 hours

## Introduction

Welcome to Lyon. This vibrant city is known for its historical significance and architectural beauty. During the project, a content presentation website will be developed, where users can read articles introducing notable heritage sites in Lyon, France. Each article is created in `.html` or `.txt` format, with front-matter embedded for metadata. Files are stored in the `content-pages` folder, which may contain nested subfolders.

Your task is to create a website that hosts these articles, following the file storage structure used for the articles.

## General Description of Project and Tasks

This project does not require a database. Content is managed through static files in the `content-pages` directory and its subfolders.

The file names follow the following format: `YYYY-MM-DD-title-in-lower-case-with-hyphens.html` or `.txt`.

Example filenames:

- `2024-09-01-example-page.html`
- `2024-10-20-greatest-lyon-heritage-site.html`
- `2025-01-01-a-post-for-future-posting.txt`

There is one central `images` folder under `content-pages`. All image paths mentioned in the articles are relative to this central images folder, regardless of their location within subfolders.

## Requirements

### Homepage

The homepage displays a list of all pages and subfolders for the users.

### URL Routes

Using the defined URL paths, users can view folder contents, display a selected page, and list pages containing a specified tag. The URLs for individual pages, subfolders, or tags are defined as follows:

**Content listing**:

- `/`: Displays the homepage with a list of all pages and subfolders.

- `/heritages/sub-folder-name` lists the pages and sub-folders inside `/sub-folder-name`

**Displaying page content**:

- `/heritages/2024-09-01-example-page-1` shows the page for `/2024-09-01-example-page-1.html` or `.txt`

- `/heritages/sub-folder-name/2024-09-02-example-page-2` shows the page for `/sub-folder-name/2024-09-02-example-page-2.html` or `.txt`

- `/tags/tag-name`: Lists pages containing the specified tag.

### Content Pages

Each content file includes:

- Optional front-matter (`---` delimited).
- Main content.

There may be different key-value pairs defined in the front-matter section. These include:

- title (optional)
- tags (optional): separated by commas, with or without spaces
- draft (optional): accepts true or other values. If the `draft` key is missing or set to any value other than `true`, the page is not considered a draft.
- summary (optional): a single-line summary used when listing pages

#### Examples

Here is an example content file in `.html` format with front-matter:

```
---
title: This is an Example Page
tags: example, test
cover: example-cover.jpeg
summary: This is a sample summary.
---

<h1>Example Page</h1>
<p>Here is the rest of the content.</p>
<p>And some other paragraph.</p>
<img src="hello-world.jpg" alt="Sample photo">
<footer>That is all</footer>
```

Here is an example content file in `.txt` format with front-matter:

```
---
title: This is another sample page
tags: example, test, plain-text
cover: another-cover.jpeg
summary: This is a sample page in txt format.
---

This is sample main content.

Each line of content is turned into <p></p> paragraph.

sample-image.jpeg

The image path / image name with individual line are turned into <img> tag.

This is footer paragraph.
```

### Page Elements and Rendering

- **Cover Image**: Cover images specified in front-matter or default to filenames in `images` folder. A radial gradient mask is applied to the cover image. The mask is a circle with its center following the mouse pointer, transitioning from black to `rgba(255,255,255,0)` with a radius of 300px. In this project, we do not need to consider the possibility of a missing cover image.

- **Title**: Determined using the following priority:

  1. If a `title` is defined in the front-matter, use it.
  2. If not, use the text content of the first `<h1>` element in the HTML content.
  3. If neither is available, derive it from the filename by removing the date and replacing hyphens with spaces, then capitalizing each word.

- **Aside Information**: Date, tags, draft status (sticky on scroll).
- **Main Content**: Dynamically loaded. HTML content renders directly. Text files render lines as paragraphs. Lines without spaces that end in a valid image extension (e.g. `.jpg`, `.png`) should be rendered as `<img>` tags. Photos expand on click, reverting on second click or scroll. First paragraph has a drop cap spanning three lines.

![Sample page](images/project-description-images/sample-page.jpg)

### Content Listing

The list shows titles and summaries, linking to individual pages. Exclude:

- Pages dated in the future.
- Draft pages
- Pages without a valid date prefix (i.e., the first 11 characters not in `YYYY-MM-DD-` format).

Subfolders are listed in alphabetical order, followed by content pages in reverse chronological order (most recent at the top).

### Search

The website must support page search functionality. Using the search field displayed in the aside on content listing pages, users should be able to search by title or content.

When a search query is submitted, the results page must display all pages whose title or content contains the query string.

It must also be possible to specify multiple keywords using the / character. In this case, the results page should list all pages whose title or content contains any of the provided keywords (i.e., a logical OR search).

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
