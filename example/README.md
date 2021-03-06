PyAnnotate example
==================

To play with this example, first install PyAnnotate:

```
pip install pyannotate
```

Then run the driver.py file:

```
python driver.py
```

Expected contents of type_info.json (after running driver.py):

```
[
    {
        "path": "gcd.py",
        "line": 1,
        "func_name": "main",
        "type_comments": [
            "() -> None"
        ],
        "samples": 1
    },
    {
        "path": "gcd.py",
        "line": 5,
        "func_name": "gcd",
        "type_comments": [
            "(int, int) -> int"
        ],
        "samples": 2
    }
]
```

Now run the pyannotate tool, like this (note the -w flag -- without
this it won't update the file):

```
pyannotate -w gcd.py
```

Expected output:

```
Refactored gcd.py
--- gcd.py        (original)
+++ gcd.py        (refactored)
@@ -1,8 +1,10 @@
 def main():
+    # type: () -> None
     print(gcd(15, 10))
     print(gcd(45, 12))
 
 def gcd(a, b):
+    # type: (int, int) -> int
     while b:
         a, b = b, a%b
     return a
Files that were modified:
gcd.py
```
