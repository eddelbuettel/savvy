# Changelog

<!-- next-header -->
## [Unreleased] (ReleaseDate)

### Breaking changes

* `savvy-cli init` now produces `Makevars.in` and `configure` instead of
  `Makevars` in order to support WebR transparently. One limitation on Windows
  is that `configure` is not set executable. This will be cared by the helper R
  package (i.e., I recommend running `savvy::savvy_init()` on an R session
  rather than using the CLI directly).

### New features

* Add an experimental support for function and environment.

## [v0.2.7] (2024-01-25)

### New features

* (Experimentally) support WebR by not using `R_UnwindProtect()`.

## [v0.2.6] (2024-01-20)

### Fixed bugs

* Fix misuses of `Rf_mkCharLenCE()` which caused compilation error on ARM64
  Linux.

## [v0.2.5] (2024-01-20)

### Breaking changes

* `ListSexp` now returns an `Sexp` instead of a `TypedSexp`. Use `.into_typed()`
  to convert an `Sexp` to a `TypedSexp`.

### New features

* Add `is_null()`.
* Add `as_read_only()` to `OwnedListSexp` as well.
* Add `cast_unchecked()` and `cast_mut_unchecked()` for casting an external
  pointer to a concrete type. Note that this is only needed for "external"
  external pointers.

## [v0.2.4] (2024-01-15)

## [v0.2.2] (2024-01-15)

### Breaking changes

* `r_print!` and `r_eprint!` are now macro that wraps `format!`, so you can use
  them just like Rust's `print!` macro. There are also `r_println!` and
  `r_eprintln!` available.

### New features

* Support scalar `usize` input.
* Add methods to access and modify attributes:
  * `get_attrib()` / `set_attrib()`
  * `get_names()` / `set_names()`
  * `get_class()` / `set_class()`
  * `get_dim()` / `set_dim()`
* A struct marked with `#[savvy]` now has `try_from()` for `Sexp`.

### Fixed bugs

* Newly-created R vectors (`Owned*Sexp`) are now properly initialized. If you
  really want to skip the initialization for some great reason, you can use
  `new_without_init()` instead of `new()`.
* `#[savvy]` now accepts `savvy::Sexp` as input.

<!-- next-url -->
[Unreleased]: https://github.com/yutannihilation/savvy/compare/v0.2.7...HEAD
[v0.2.7]: https://github.com/yutannihilation/savvy/compare/v0.2.6...v0.2.7
[v0.2.6]: https://github.com/yutannihilation/savvy/compare/v0.2.5...v0.2.6
[v0.2.5]: https://github.com/yutannihilation/savvy/compare/v0.2.4...v0.2.5
[v0.2.4]: https://github.com/yutannihilation/savvy/compare/savvy-v0.2.2...v0.2.4
[v0.2.2]: https://github.com/yutannihilation/savvy/compare/savvy-v0.2.1...savvy-v0.2.2