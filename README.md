# Steps to reproduce pyright issue with conda env

1. Create a virtual env with `conda create -n test python=3.6 numpy`
2. Find the env location with `conda info --envs`
3. Modify the paths in `pyrightconfig.json` correspondingly.
4. Start emacs and verify in `lsp-log` buffer, the python exe path is the one we assigned.

# Current issue

1. Assign the env with is working but auto completion and jump to definition is not working.
   ```emacs-lisp
   (lsp-register-custom-settings
   `(("python.pythonPath" "/Users/ztlevi/.conda/envs/test/bin/python")
      ("python.venvPath" "/Users/ztlevi/.conda/envs/test")))
   ```
1. Assigne wtith the `pyrightconfig.json` file, the pytho exe path is not correct and auto completion is not working.
