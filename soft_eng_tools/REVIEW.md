# Pull Request Review Rules

This file defines the rules and patterns to check when reviewing GitHub pull
requests. These are primarily Fortran coding standards for this project. When
reviewing a PR, check the changed code against every rule below and flag any
violation with the specific file and line number.

For each finding, cite the rule it violates, point to the exact location, and
suggest the corrected code where possible.

## Rules

1. **No module-level `save`.** Do not use the `save` attribute (or implicit
   `save` via initialization) on module-level variables.

2. **Minimal-scope `use` statements.** `use` statements should be placed at the
   lowest necessary scope (e.g., inside the subroutine/function that needs them)
   rather than at module level, whenever practical.

3. **Label `pure` where applicable.** Subroutines and functions should be
   labeled `pure` when they satisfy the "pure" requirements defined in the
   Fortran standard.

4. **Use full block-end keywords.** Use `end do` instead of `enddo`, and
   `end if` instead of `endif`.

5. **Use Modern Fortran syntax.** Prefer modern Fortran operators and syntax
   (e.g., `>` instead of `.gt.`, `>=` instead of `.ge.`, `==` instead of `.eq.`,
   etc.).

6. **Namelist XML header comment.** Make sure namelist XML files include the
   standard comment block at the beginning of the file.

7. **Checked `allocate` calls.** Make sure all `allocate` calls return both
   `stat` and `errmsg`. In a physics scheme, a non-zero `stat` must cause the
   routine to return with correctly set `ccpp_error_code` and
   `ccpp_error_message` variables.

8. **Citations need DOIs.** Make sure all citations include a DOI, or if a DOI
   is unavailable, as close to a full citation as possible.

9. **Grammatical comments.** Check that all full-sentence comments are
   grammatically correct.

10. **Single-output subroutines → functions.** Convert any subroutine that has
    only a single output variable into a function.

11. **Character arguments use `len=*`.** Make sure all character-type subroutine
    arguments are declared with `len=*`, unless they are declared as an
    `allocatable` or `pointer` within the subroutine itself.

12. **No `goto`.** Make sure all `goto` and `go to` statements have been removed.
