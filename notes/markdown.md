## Markdown

#### What is markdown?

Markdown is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown.

File extentions: `.md` or `.markdown`

#### Table of contents

1. [Text](#Text)
1. [Lists](#Lists)
1. [Images](#Images)
1. [Headers and Quotes](#Headers)
1. [Code](#Code)
1. [Tables](#Tables)
1. [Extras](#Extras)

#### Text

**bold**: `**text**` or `__text__`
_italic_: `*text*` or `_text_`
[link](http://google.com): `[link](http://google.com)`
**h5 tag**: `##### h5 tag`
~~strikethrough~~: `~~strikethrough~~`

#### Lists

**Unordered** lists can be created using `*` or `-` where _identation_ creates different levels
`* Start a line with a star`
`* Profit!`

-   Start a line with a star
-   Profit!

`1. Start a line with a star`
`1. Profit!`

1. Start a line with a number
1. Profit!

#### Images

template: `![alt](href)`
example: `![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)`
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

#### Headers and Quotes

Create **_Headers_** using 1-6 `#` + text
Create **_Quotes_** using `>` symbol

```md
> Coffee. The finest organic suspension ever devised... I beat the Borg with it.
>
> -   Captain Janeway
```

Output:

> Coffee. The finest organic suspension ever devised... I beat the Borg with it.
>
> -   Captain Janeway

#### Code

Inline code blocks:

> \`var example = true\`

Multiline code:

> \```javascript
> var example = 1;
> console.log(example);
> \```

#### Tables

You can create tables by assembling a list of words and dividing them with hyphens `-` (for the first row), and then separating each column with a pipe `|`:

```
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
```

| First Header                | Second Header                |
| --------------------------- | ---------------------------- |
| Content from cell 1         | Content from cell 2          |
| Content in the first column | Content in the second column |

#### Extras

-   [Emojis cheatsheet](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md)
-   Reference users with `@user`
-   ![purple](https://placehold.it/15/e9b6b3/000000?text=+) no learning resources assigned Color boxes `![white](https://placehold.it/15/F9F9F2/000000?text=+) text`
-   Tasks lists are my favorite:

```markdown
-   [x] This is a complete item
-   [ ] This is an incomplete item
```

-   [x] This is a complete item
-   [ ] This is an incomplete item

#### References

-   https://guides.github.com/features/mastering-markdown/
-   https://www.markdowntutorial.com/lesson/1/
