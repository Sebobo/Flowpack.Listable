# Listable

This Neos package solves one problem: help you list any nodes in TypoScript.
The idea is very simple: you often need to display list of things (e.g. news, articles etc), and the concern of listing items should better be separated from the concern of rendering items. This packages provides a solid foundation for listing, while allowing you to take care of rendering stuff on your own.

# TL;DR

1. Add `Sfi.Listable:ListableMixin` to nodetypes that you want to list
2. Build your list based on `Sfi.Listable:Listable` for simple list or on `Sfi.Listable:List` for list with a header and an archive link.
3. Rely on public API keys when overriding settings.

[See here](https://github.com/sfi-ru/KateheoDistr/blob/master/Packages/Sites/Sfi.Kateheo/Resources/Private/TypoScript/NodeTypes/PageMain.ts2#L5) for a trivial integration example.

# Nodetype mixins

On data level we provide only one mixin: `Sfi.Listable:ListableMixin`. The only thing you have to do, is to add this mixin to nodetypes that you would want to list with this package. That's right, planing all other fields is completely up to you.

# TypoScript objects

Keys documented here are considered public API and would be treated with semantic versioning in mind. Extend all other properties at your own risk.

## Sfi.Listable:Listable

At the heart of this package is a `Sfi.Listable:Listable` object. It provides some good defaults for rendering lists of things, and is pretty extensible too. Here are TypoScript context variables that you can configure for this object:

| Setting | Description | Defaults |
|---------|-------------|----------|
| listClass | Classname of UL tag | '' |
| itemClass | Classname of LI tag of wrapping each item | '' |
| sortProperty | Sort by property | 'date' |
| sortOrder | Sort order | 'DESC' |
| limit | Limit number of results. Set to high number when using with pagination | 10000 |
| paginationEnabled | Enable pagination | true |
| itemsPerPage | Number of items per page when using pagination | 24 |
| maximumNumberOfLinks | Number of page links in pagination | 15 |
| queryType | Predefined query types, choose between `getFromCurrentPage` and `getAll` | 'getAll' |
| itemRenderer | Object used for rendering child items | 'Sfi.Listable:ContentCaseShort' |

## Sfi.Listable:List

There's often a need to render a list with a header an a archive link.
This object takes `Sfi.Listable:Listable` and wraps it with just that.

| Setting | Description | Defaults |
|---------|-------------|----------|
| wrapClass | Class of a div that wraps the whole object | '' |
| listTitle | Test of a title | '' |
| listTitleClass | Class of a list title | '' |
| archiveLink | Nodepath for archive link | '' |
| archiveLinkTitle | Title of an archive link | '' |
| archiveLinkClass | Classname of an archive link | '' |
