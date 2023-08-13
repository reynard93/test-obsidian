 launchctl unload -w ~/Library/LaunchAgents/emacs_work.plist
load to do the opposite
launchctl list | grep -i emacs -> check if your daemon is running

```

;;; init.el -*- lexical-binding: t no-byte-compile: t -*-

;; Copyright (C) 2021-2023 zilongshanren

;; Author: zilongshanren <guanghui8827@gmail.com>
;; URL: https://github.com/zilongshanren/emacs.d


;; This file is not part of GNU Emacs.
;;
;; This program is free software; you can redistribute it and/or
;; modify it under the terms of the GNU General Public License as
;; published by the Free Software Foundation; either version 3, or
;; (at your option) any later version.
;;
;; This program is distributed in the hope that it will be useful,
;; but WITHOUT ANY WARRANTY; without even the implied warranty of
;; MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
;; General Public License for more details.
;;
;; You should have received a copy of the GNU General Public License
;; along with this program; see the file COPYING.  If not, write to
;; This buffer is for text that is not saved, and for Lisp evaluation.
;; To create a file, visit it with \ f f and enter text in its buffer.
;; the Free Software Foundation, Inc., 51 Franklin Street, Fifth
;; Floor, Boston, MA 02110-1301, USA.
;;


;; part of the code are from Centaur emacs
;;; Code:
;; (require 'cl-lib)
;; run M-x profiler-report to see what is hogging
;; (require 'profiler)
;; (profiler-start 'cpu)

;; Speed up startup
(setq auto-mode-case-fold nil)

(setq gc-cons-threshold most-positive-fixnum
      gc-cons-percentage 0.5)
(add-hook 'emacs-startup-hook
          (lambda ()
            "Recover GC values after startup."
            (setq gc-cons-threshold 80000000
                  gc-cons-percentage 0.1)))


;; Faster to disable these here (before they've been initialized)
(push '(menu-bar-lines . 0) default-frame-alist)
(push '(tool-bar-lines . 0) default-frame-alist)
(push '(vertical-scroll-bars) default-frame-alist)
(when (featurep 'ns)
  (push '(ns-transparent-titlebar . t) default-frame-alist))

(setenv "PATH" (concat (getenv "PATH") ":/sw/bin"))
(setq exec-path (append exec-path '("/sw/bin")))

(defun set-exec-path-from-shell-PATH ()
  "Set up Emacs' `exec-path' and PATH environment variable to match
that used by the user's shell.

This is particularly useful under Mac OS X and macOS, where GUI
apps are not started from a shell."
  (interactive)
  (let ((path-from-shell (replace-regexp-in-string
			  "[ \t\n]*$" "" (shell-command-to-string
					  "$SHELL --login -c 'echo $PATH'"
						    ))))
    (setenv "PATH" path-from-shell)
    (setq exec-path (split-string path-from-shell path-separator))))

(set-exec-path-from-shell-PATH)

;;Load path
;;Optimize: Force "lisp"" and "site-lisp" at the head to reduce the startup time.
(defun update-load-path (&rest _)
  "Update `load-path'."
  (dolist (dir '("site-lisp" "lisp"))
    (push (expand-file-name dir user-emacs-directory) load-path)))

(defun add-subdirs-to-load-path (&rest _)
  "Add subdirectories to `load-path'."
  (let ((default-directory (expand-file-name "site-lisp" user-emacs-directory)))
    (normal-top-level-add-subdirs-to-load-path)))

(advice-add #'package-initialize :after #'update-load-path)
(advice-add #'package-initialize :after #'add-subdirs-to-load-path)

(update-load-path)

;; Packages
;; Without this comment Emacs25 adds (package-initialize) here
(require 'init-package)

;; Core
(require 'init-basic)
(require 'init-completion)

;; (require 'init-evil)

(require 'init-tools)
(require 'init-writing)
;;(require 'init-reading)

;; uis
(require 'init-ui)
(require 'init-window)
(require 'init-better-defaults)

;; Tools
(require 'init-org)
(require 'init-git)
(require 'init-ctags)
(require 'init-syntaxcheck)
(require 'init-snippets)

(require 'init-lsp)

;; Frameworks
;; yaml init , shell etc
;; init-prog.el
(require 'init-web)
(require 'init-gpu)
(require 'init-persp)


;; Languages
(require 'init-lisp)
(require 'init-csharp)
(require 'init-javascript)
(require 'init-rust)
(require 'init-python)
(require 'init-c)
(require 'init-dart)
(require 'init-elixir)

;; personal
(require 'init-keybindings)
;; ai
(require 'init-ai)

;; programming
(require 'init-programming)
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;; init.el ends here
(put 'dired-find-alternate-file 'disabled nil)

```