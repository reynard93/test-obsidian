
my overlays are
```
{ system, inputs, ... }:

[

  inputs.emacs-overlay.overlays.default

  # -------------------------------------------------------------------------------------------------------

  (final: prev: {

    emacs-29 = (prev.emacsGit.overrideAttrs (old:
      let major = "30";
      in {
        name = "emacs-${major}";
        version = inputs.emacs-src.shortRev;
        src = inputs.emacs-src;
        patches = [
          "${inputs.emacs-plus}/patches/emacs-${major}/system-appearance.patch"
          "${inputs.emacs-plus}/patches/emacs-${major}/no-frame-refocus-cocoa.patch"
          "${inputs.emacs-plus}/patches/emacs-${major}/round-undecorated-frame.patch"
          "${inputs.emacs-plus}/patches/emacs-${major}/fix-window-role.patch"
        ];

        # wasn't this merged into mainline?
        configureFlags = old.configureFlags ++ [
          "--enable-check-lisp-object-type"
          # "--with-native-compilation=aot"
        ];

      })).override {

        stdenv = prev.addAttrsToDerivation {
          NIX_CFLAGS_COMPILE =
            "-mcpu=native -O3 -pipe -ftree-vectorize -fomit-frame-pointer -DFD_SETSIZE=10000 -DDARWIN_UNLIMITED_SELECT";
          BYTE_COMPILE_EXTRA_FLAGS = ''
            --eval '(setq native-comp-speed 3)'
            --eval '(setq native-comp-compiler-options '("-O3" "-ftree-vectorize" "-fomit-frame-pointer"))'
          '';
        } (prev.impureUseNativeOptimizations final.llvmPackages_14.stdenv);

      };
  })
]
```


1. my inputs are
    
    123    `emacs-overlay.url = "github:Nix-Community/emacs-overlay";     emacs-plus.url = "github:d12frosted/homebrew-emacs-plus";     emacs-src.url = "github:emacs-mirror/emacs/emacs-29";`
    
    12    `emacs-src.flake = false;     emacs-plus.flake = false;`
	