# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

<!-- ## [Unreleased] -->

## [1.0.1] - 2018-02-01
- Always parameterize `Promise`. In Closure `Promise` is valid, but in TypeScript this is invalid and must be `Promise<any>` instead.
- Escape `*\` comment end sequences when formatting comments. These turn up in practice when an HTML comment embeds a JavaScript style block comment, like here: https://github.com/PolymerElements/paper-icon-button/blob/master/paper-icon-button.html#L51
- Hybrid Polymer elements without a LHS assignment now have `Element` appended to their generated interface name, to match the behavior of the Closure Polymer Pass (https://github.com/google/closure-compiler/wiki/Polymer-Pass#element-type-names-for-1xhybrid-call-syntax). For example, `interface IronRequest` is now `interface IronRequestElement`.
- Typings are now emitted for all HTML files, even if they contain no script tags. Added `index.html` to the default `exclude` set (alongside the existing `test/**` and `demo/**` globs).

## [1.0.0] - 2018-01-25
- [BREAKING] The `--outDir` flag is now required when using the command line tool. Previously it would print all concatenated typings to `stdout`, which doesn't make much sense given that we emit multiple files.
- Rewrite triple-slash references to Polymer into the `types/` directory so that they resolve correctly. Polymer is a special case where we put the typings in a `types/` subdirectory in order not to clutter the repo.
- Emit a `const FooBehavior: object` for behaviors. This lets TypeScript know that e.g. `Polymer.AppLocalizeBehavior` is a valid symbol that could be passed, for example, to the `Polymer.mixinBehaviors` function.

## [0.3.6] - 2018-01-09
- Support parameterized types other than `Array` and `Object`, such as `Foo<T>`.

## [0.3.5] - 2018-01-02
- Properties are now emitted as `readonly` when applicable.
- Bump Analyzer for latest scanning features (getters/setters, static methods, methods/properties on class prototypes).

## [0.3.4] - 2017-12-20
- Handle optional and rest parameters in function type expressions.

## [0.3.3] - 2017-12-18
- Pin Analyzer version for upcoming major refactor.

## [0.3.2] - 2017-12-18
- Static methods are now supported on classes, elements, and mixins.
- Add `renameTypes` config option, a map of renames to apply to named types that can be configured per-project.
- Convert Closure `ITemplateArray` type to TypeScript `TemplateStringsArray`.
- Support object index signatures (e.g. `Object<foo, bar>` maps to `{[key: foo]: bar}`).

## [0.3.1] - 2017-12-15
- Convert Closure `Object` to TypeScript `object`.
- Use glob patterns instead of RegExps to exclude files.
- Bump Analyzer version to include https://github.com/Polymer/polymer-analyzer/pull/791 which makes Polymer properties possibly `null|undefined`.

## [0.3.0] - 2017-12-12
- `void` is not nullable.
- Support constructor functions (e.g. `function(new:HTMLElement, string)`).
- Support record types (e.g. `@param {{foo: bar}}`).
- Include method `@return` descriptions.

## [0.2.0] - 2017-12-08
- Many fixes. See https://github.com/Polymer/gen-typescript-declarations/issues/23.

## [0.1.0] - 2017-11-09
- Initial release on NPM.
