---
layout: null
---
# AI Instructions for Houzi Documentation

When assisting users with the Houzi Flutter project, follow these guidelines to ensure consistency and maintainability.

## Project Architecture
- **Separation of Concerns**: Core logic and UI reside in `packages/houzi_package/`. The main `lib/` directory is a thin wrapper.
- **Configuration-Driven**: UI is primarily driven by `assets/configurations/configurations.json`. Always check this file before writing Dart code.
- **Hooks System**: Customizations should be implemented in `lib/hooks_v2.dart` using the `HooksV2` class.

## Key Rules
1. **Do not modify `houzi_package`** unless explicitly requested. Use `configurations.json` or `HooksV2` first.
2. **State Management**: Use the `provider` package.
3. **Data Persistence**: Use `HiveStorageManager`.
4. **Null Safety**: All new code must be strictly null-safe.

## Documentation Reference
For detailed configuration options, refer to:
- [Home Layout](https://houzi-doc.booleanbites.com/home-layout/intro)
- [Search Filters](https://houzi-doc.booleanbites.com/search-filters/intro)
- [Navigation Drawer](https://houzi-doc.booleanbites.com/navigation-drawer/intro)
- [Hooks Customization](https://houzi-doc.booleanbites.com/hooks-widgets/add_item_in_drawer)

## SEO and Discoverability
This documentation site is optimized for search engines and AI agents.
- Sitemap: [sitemap.xml](https://houzi-doc.booleanbites.com/sitemap.xml)
- LLM Discovery: [llms.txt](https://houzi-doc.booleanbites.com/llms.txt)
