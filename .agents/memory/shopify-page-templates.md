---
name: Shopify page links vs templates
description: theme page templates alone don't make /pages/<handle> routes resolve
---
Liquid theme files like `templates/page.privacy.liquid` only render *if* a Shopify Page record with a matching handle exists in the store's Admin (Online Store > Pages) and is assigned that template. Creating/editing the `.liquid` template file is a theme-code change; it does not create the Page record itself — that's store content, managed in Shopify Admin, and can't be done from the theme codebase alone.

**Why:** A footer/nav link to `/pages/<handle>` will 404 in the live store if the merchant hasn't created the corresponding Page in Admin, even when the template file with full content already exists in the theme.

**How to apply:** When asked to "fix" or "add content to" footer/nav policy pages, check whether `templates/page.<handle>.liquid` already exists with real content first (it often already does in this theme). If so, the remaining step is telling the user to create/assign the Page in Shopify Admin — that's outside what theme-code changes can accomplish.
