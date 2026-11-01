# ArrayUtils provenance

Reviewed 2026-10-31:

- [Joe's REALbasic Page](https://strout.net/info/coding/rb/intro.html) introduces
  the array utilities and invites readers to use the code in their projects.
- [Original archive](https://www.strout.net/files/rb/arrayutils.zip), downloaded
  over HTTPS, contains the binary REALbasic project `ArrayUtils.rbp`.
- Download SHA-256: `792d4452a46f04838bf70983e4ae3ba4ea640478fc16829edff258f9ca6f3adf`.

The project's embedded source strings were inspected directly, including its
unit tests and all eleven distinct operation names. This Buoy implementation
was written independently against those operations and their documented range
conventions. The original archive, binary project, menus, and app assets are not
redistributed. The landing page specifically calls StringUtils public domain;
this document does not infer that same designation for ArrayUtils.

Implemented operations: numeric Total/Average/Min/Max, signed half-open Slice,
RemoveSlice, Splice, whole-array append (`AppendAll`), and in-place Reverse.
Clone/Concat already exist in Buoy's Array namespace. The implementation is
generic for structural operations instead of repeating separate Integer, Double,
and String versions. It validates invalid/reversed ranges, defines empty means
as zero (matching the supplied original unit tests), snapshots aliasing source
arrays, and respects Buoy's fixed/resizable array distinction. These differences
are intentional; it is not a byte-for-byte translation of the historical project.
