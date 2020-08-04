Debug trap on platforms
================================
| Architecture       | debug_break() |
| -------------      | ------------- |
| x86/x86-64         | `int3`  |
| ARM mode, 32-bit   | `.inst 0xe7f001f0`  |
| Thumb mode, 32-bit | `.inst 0xde01`  |
| AArch64, ARMv8     | `.inst 0xd4200000` |
| MSVC compiler      | `__debugbreak` |
| Apple compiler on AArch64     | `__builtin_trap()` |

Basic SKIA drawing
================================
  SkRect r = SkRect::MakeXYWH(0, 0, w_, h_);
  SkPaint p;
  p.setColor(0xFFFFFFFF);
  p.setStyle(SkPaint::kFill_Style);
  canvas->drawRect(r, p);
