---
title: Documentation Style Test
description: A temporary page demonstrating supported documentation styles.
category: Examples
order: 1
slug: style-test
---

This introduction demonstrates **bold text**, *italic text*, ~~strikethrough~~, `inline code`, and [external links](https://example.com).

## Headings

### Third-level heading

#### Fourth-level heading

Normal paragraphs support standard Markdown formatting and line wrapping.

> This is a blockquote.
>
> It can contain **formatted text** and multiple paragraphs.

---

## Lists

Unordered list:

- First item
- Second item
  - Nested item
  - Another nested item
- Third item

Ordered list:

1. Install the project.
2. Configure the environment.
3. Start the application.

Task list:

- [x] Create the documentation page
- [x] Add syntax highlighting
- [ ] Remove this temporary page later

## Table

| Feature | Supported | Notes |
| --- | :---: | --- |
| Markdown | Yes | GitHub-flavoured Markdown |
| Accordions | Yes | Custom accordion blocks |
| Code highlighting | Yes | Language-aware fenced blocks |
| Relative links | Yes | Markdown documents become docs routes |
| Relative images | Yes | Loaded from the repository |

## Accordion

:::accordion What can an accordion contain?

Accordion bodies support normal Markdown.

- Lists
- **Formatting**
- Links
- Inline `code`
- Fenced code blocks

```typescript
type DocumentationPage = {
  title: string;
  category: string;
  order: number;
};

const page: DocumentationPage = {
  title: 'Style Test',
  category: 'examples',
  order: 1
};
```

:::

:::accordion Another example

> Accordions can also contain quotes, tables, images, and other Markdown elements.

| Setting | Value |
| --- | --- |
| Theme | Portfolio |
| Rendering | Markdown |
| Repository | `seailz/docs` |

:::

## JavaScript

```javascript
async function loadDocumentation() {
  const response = await fetch('/api/docs');

  if (!response.ok) {
    throw new Error(`Request failed: ${response.status}`);
  }

  return response.json();
}

const documentation = await loadDocumentation();
console.log(documentation);
```

## Java

```java
public final class Documentation {
    private final String title;
    private final String category;

    public Documentation(String title, String category) {
        this.title = title;
        this.category = category;
    }

    public String title() {
        return title;
    }
}
```

## JSON

```json
{
  "title": "Documentation Style Test",
  "category": "examples",
  "order": 1,
  "published": true
}
```

## Shell

```bash
git add test-post.md
git commit -m "docs: add temporary style test"
git push
```

## SQL

```sql
SELECT title, category
FROM documentation
WHERE published = TRUE
ORDER BY position ASC;
```

## Relative content

Link to another document:

[Open the installation guide](./installation.md)

Display an image stored beside this page:

![Example screenshot](./images/example.png)

## Raw HTML details

Standard HTML is also accepted:

<details>
<summary>Native HTML details element</summary>

This is a native HTML details block.

</details>
