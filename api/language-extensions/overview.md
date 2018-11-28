---
---

# Language Extension Overview

Visual Studio Code provides smart editing features for different programming languages through Language Extensions. VS Code doesn't provide built-in language support but offers a set of APIs that enable rich language features. For example, it is a bundled [HTML](https://github.com/Microsoft/vscode/tree/master/extensions/html) extension that allows VS Code to show syntax highlighting for HTML files. Similarly, when you type `console.` and `log` shows up in IntelliSense, it is the [Typescript Language Features](https://github.com/Microsoft/vscode/tree/master/extensions/typescript-language-features) extension at work.

Smart editing features can be roughly put into two categories:

## Declarative language support

Declarative language editing support is defined in configuration files. Examples include [html](https://github.com/Microsoft/vscode/tree/master/extensions/html), [css](https://github.com/Microsoft/vscode/tree/master/extensions/css) and [typescript-basic](https://github.com/Microsoft/vscode/tree/master/extensions/typescript-basics) extensions bundled with VS Code, which offer a subset of the following Declarative Language Features:

- Syntax highlighting
- Snippet completion
- Bracket matching
- Bracket autoclosing
- Bracket autosurrounding
- Comment toggling
- Folding (legacy)

We have three guides for writing Language Extensions that provide Declarative Language Features.

- [Syntax Highlight Guide](/api/language-extensions/syntax-highlight-guide): VS Code uses TextMate grammar for syntax highlighting. This guide will walk you through converting an existing TextMate grammar into a VS Code extension.
- [Snippet Completion Guide](/api/language-extensions/snippet-guide): Extension authors can provide handy snippets for any language. Learn how to add an idiomatic framework usage as a snippet, or create a snippet for using the latest ECMAScript syntax.
- [Language Configuration Guide](/api/language-extensions/language-configuration-guide): VS Code allows extensions to define a **language configuration** for any programming language. This file controls basic editing features such as comment toggling, bracket matching/surrounding and region folding (legacy).

## Programmatic language features

Programmatic Language Features include auto completion, error checking, and jump to definition. These features are often powered by a Language Server, a program that analyzes your project to provide the dynamic features.
 One example is the [`typescript-language-features`](https://github.com/Microsoft/vscode/tree/master/extensions/typescript-language-features) extension bundled in VS Code. It utilizes the [TypeScript Language Service](https://github.com/Microsoft/TypeScript/wiki/Using-the-Language-Service-API) to offer Programmatic Language Features such as:

- Hover information ([`vscode.languages.registerHoverProvider`](https://code.visualstudio.com/docs/extensionAPI/vscode-api#languages.registerHoverProvider))
- Auto completion ([`vscode.languages.registerCompletionItemProvider`](https://code.visualstudio.com/docs/extensionAPI/vscode-api#languages.registerCompletionItemProvider))
- Jump to definition ([`vscode.languages.registerDefinitionProvider`](https://code.visualstudio.com/docs/extensionAPI/vscode-api#languages.registerDefinitionProvider))
- Error checking
- Formatting
- Refactoring

For a complete list of Programmatic Language Features, see [Language Features](/api/language-extensions/language-features).

![multi-ls](images/overview/multi-ls.png)

## Language Server Protocol

By standardizing the communication between a Language Server (a static code analysis tool) and a Language Client (usually a source code editor), the [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) allows extension authors to write one code analysis program and reuse it in multiple editors.

In the [Language Features](/api/language-extensions/language-features) listing, you can find a listing of all VS Code language features and how they map to the [Language Server Protocol Specification](https://microsoft.github.io/language-server-protocol/specification).

There are also two in-depth guides that explain two approaches for extension authors to implement rich language features in VS Code:

- [Smart Editing Guide](/api/language-extensions/smart-editing-guide)
- [Smart Editing LSP Guide](/api/language-extensions/smart-editing-lsp-guide)

![multi-editor](images/overview/multi-editor.png)

## Special cases

### Multi-root workspace support

When the user opens a [multi-root workspace](/docs/editor/multi-root-workspaces), you might need to adapt your Language Server extensions accordingly. This topic discusses multiple approaches to supporting multi-root workspaces.

### Embedded languages

Embedded languages are common in web development. For example, CSS/JS inside HTML, and GraphQL inside JavaScript/TypeScript. This topic discusses how you can make language features available to embedded languages.