To find where Python is installed on Linux Mint, you can use the following methods:

### 1. **Using the `which` command**

The `which` command locates the executable path of Python:

```bash
which python
```

Or, if you're using a specific version:

```bash
which python3
which python3.x  # Replace 'x' with the minor version, e.g., python3.10
```

### 2. **Using the `whereis` command**

The `whereis` command provides all the paths related to Python:

```bash
whereis python
```

Or:

```bash
whereis python3
```

### 3. **Using the `command -v` command**

This is another way to find the path to the Python executable:

```bash
command -v python
```

Or:

```bash
command -v python3
```

### 4. **Using Python itself**

Run Python and check its installation path:

```bash
python --version  # Ensure Python is installed
python -c "import sys; print(sys.executable)"
```

Or for Python 3:

```bash
python3 --version
python3 -c "import sys; print(sys.executable)"
```

### 5. **Searching the filesystem**

If you suspect Python might not be in the default `PATH`, you can search the entire filesystem:

```bash
sudo find / -name "python*" 2>/dev/null
```

Choose the method that works best for your situation! Let me know if you need further assistance.