# Steps to reproduce pyright issue with conda env

1. Create a virtual env with `conda create -n test python=3.6 numpy`
2. Find the env location with `conda info --envs`
3. Modify the paths in `pyrightconfig.json` correspondingly.
4. Start emacs and verify in `lsp-log` buffer, the python exe path is the one we assigned.

# Current issue

1. Assign the env with `lsp-register-custiom-settings`

   ```emacs-lisp
   (lsp-register-custom-settings
   `(("python.pythonPath" "/Users/ztlevi/.conda/envs/test/bin/python")
      ("python.venvPath" "/Users/ztlevi/.conda/envs/test")))
   ```

   - The env path in lsp-log
     ```
     Found 4 source files
     No configuration file found.
     Setting pythonPath for service "python_test": "/Users/ztlevi/.conda/envs/test/bin/python"
     ```
   - auto completion and jump to definition is not working.

2. Assigne wtith the `pyrightconfig.json` file.

   - The env path in lsp-log

     ```
     Found 4 source files
     No configuration file found.
     Setting pythonPath for service "python_test": "/usr/local/bin/python3"
     ```

   - auto completion and jump to definition is not working.
