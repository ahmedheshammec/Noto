
Here's the Exact Error:
error: command '/usr/bin/clang++' failed with exit code 1

Full Traceback: 

```
Collecting PyKCS11==1.5.18
  Using cached pykcs11-1.5.18.tar.gz (105 kB)
  Installing build dependencies: started
  Installing build dependencies: finished with status 'done'
  Getting requirements to build wheel: started
  Getting requirements to build wheel: finished with status 'done'
  Preparing metadata (pyproject.toml): started
  Preparing metadata (pyproject.toml): finished with status 'done'
Building wheels for collected packages: PyKCS11
  Building wheel for PyKCS11 (pyproject.toml): started
  Building wheel for PyKCS11 (pyproject.toml): finished with status 'error'
Failed to build PyKCS11

  error: subprocess-exited-with-error
  
  × Building wheel for PyKCS11 (pyproject.toml) did not run successfully.
  │ exit code: 1
  ╰─> [28 lines of output]
      /private/var/folders/6_/3yjt36f92k1bf19vfgd123rc0000gn/T/pip-build-env-5t7_sqve/overlay/lib/python3.11/site-packages/setuptools/dist.py:759: SetuptoolsDeprecationWarning: License classifiers are deprecated.
      !!
      
              ********************************************************************************
              Please consider removing the following classifiers in favor of a SPDX license expression:
      
              License :: OSI Approved :: GNU General Public License (GPL)
      
              See https://packaging.python.org/en/latest/guides/writing-pyproject-toml/#license for details.
              ********************************************************************************
      
      !!
        self._finalize_license_expression()
      running bdist_wheel
      running build
      running build_py
      running build_ext
      building 'PyKCS11._LowLevel' extension
      swigging src/pykcs11.i to src/pykcs11_wrap.cpp
      swig -python -c++ -o src/pykcs11_wrap.cpp src/pykcs11.i
      creating build/temp.macosx-15.0-arm64-cpython-311/src
      clang++ -Wsign-compare -Wunreachable-code -DNDEBUG -g -fwrapv -O3 -Wall -I/opt/homebrew/opt/ruby/include -Isrc -I/usr/local/include "-I/Volumes/Samsung T5/Odoo/Development & Study/odoo15/.venv/include" -I/Users/ahmed/.pyenv/versions/3.11.10/include/python3.11 -c src/ck_attribute_smart.cpp -o build/temp.macosx-15.0-arm64-cpython-311/src/ck_attribute_smart.o
      In file included from src/ck_attribute_smart.cpp:18:
      src/stdafx.h:27:10: fatal error: 'vector' file not found
         27 | #include <vector>
            |          ^~~~~~~~
      1 error generated.
      error: command '/usr/bin/clang++' failed with exit code 1
      [end of output]
  
  note: This error originates from a subprocess, and is likely not a problem with pip.
  ERROR: Failed building wheel for PyKCS11
ERROR: Could not build wheels for PyKCS11, which is required to install pyproject.toml-based projects

[notice] A new release of pip is available: 24.0 -> 25.3
[notice] To update, run: pip install --upgrade pip
```

## ✅ The real fix (explicit libc++ include)

Run **exactly this**:

```
export SDKROOT="$(xcrun --show-sdk-path)"
export CXXFLAGS="-isysroot $SDKROOT -stdlib=libc++ -I$SDKROOT/usr/include/c++/v1"
export CPPFLAGS="-isysroot $SDKROOT -I$SDKROOT/usr/include/c++/v1"
```

Verify it exists:

```
ls "$SDKROOT/usr/include/c++/v1/vector"
```

Force xcrun clang++

```
export CC="xcrun clang"
export CXX="xcrun clang++"
```

Install PyKCS11

```
pip install --no-cache-dir PyKCS11==1.5.18
```

