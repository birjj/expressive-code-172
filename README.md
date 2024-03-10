# Astro Starter Kit: Basics

To reproduce the issue:

1. Run `npm install`
1. Run `npx @astrojs/upgrade`, or upgrade Astro in `package.json`:
    ```diff
    "dependencies": {
    +   "astro": "^4.4.15",
        "astro-expressive-code": "^0.26.2",
        "@expressive-code/plugin-collapsible-sections": "^0.26.2",
        "typescript": "^5.4.2"
    }
    ```
2. Change `package.json` to newest versions of all packages, while removing `@expressive-code/plugin-collapsible-sections`:
    ```diff
    "dependencies": {
        "astro": "^4.4.15",
    +   "astro-expressive-code": "^0.33.4",
    -   "@expressive-code/plugin-collapsible-sections": "^0.26.2",
        "typescript": "^5.4.2"
    }
    ```
3. Run `npm install`
4. Visit `/test`