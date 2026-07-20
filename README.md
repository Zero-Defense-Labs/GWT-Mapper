# GWT-Mapper

GWT-Mapper is a reconnaissance tool for **Google Web Toolkit (GWT)** applications that statically analyzes compiled GWT JavaScript to enumerate exposed RPC interfaces, methods, services, and GWTP Dispatch actions.

This version extends the original project with improved support for modern GWT applications, including **GWT 2.7+ ServiceHelper serialization**, **GWTP Dispatch**, concurrent deferred-fragment enumeration, and enhanced RPC reconstruction.

## Features

* Enumerate GWT-RPC services and methods
* Support for GWT bootstrap (`*.nocache.js`) and permutation (`*.cache.js`) files
* Automatic permutation discovery
* Deferred fragment downloading with concurrent requests
* Generate serialized GWT-RPC request templates
* Optional live RPC probe requests
* Enumerate GWTP Dispatch Action classes
* Detect GWT 2.7+ ServiceHelper serialization pattern
* Recover DispatchService operations
* HTTP Basic Authentication support
* Cookie and proxy support
* Filter methods by name
* Save cleaned JavaScript for offline analysis
* Quiet mode and colored output

---

## Installation

```bash
git clone <repository>
cd GWTMap
pip install requests
```

Python 3.8+ is recommended.

---

## Usage

```bash
python3 gwtmap.py -u https://target/app/app.nocache.js
```

### Offline analysis

```bash
python3 gwtmap.py -F 0123456789ABCDEF0123456789ABCDEF.cache.js
```

---

## Command Line Options

| Option      | Description                                   |
| ----------- | --------------------------------------------- |
| `-u`        | Target GWT bootstrap or permutation URL       |
| `-F`        | Analyze a local permutation file              |
| `-b`        | Specify module base URL                       |
| `-p`        | HTTP proxy                                    |
| `-c`        | Cookies                                       |
| `--basic`   | HTTP Basic Authentication                     |
| `--rpc`     | Generate serialized GWT-RPC requests          |
| `--probe`   | Send generated RPC requests                   |
| `--svc`     | Show discovered services                      |
| `--actions` | Enumerate GWTP Dispatch Action classes        |
| `--code`    | Dump formatted JavaScript                     |
| `--backup`  | Save retrieved JavaScript                     |
| `--filter`  | Filter output                                 |
| `-t`        | Concurrent deferred-fragment download threads |
| `-q`        | Quiet mode                                    |
| `--color`   | Colored output                                |

---

## Examples

Enumerate methods:

```bash
python3 gwtmap.py -u https://target/app/app.nocache.js
```

Generate RPC payloads:

```bash
python3 gwtmap.py -u https://target/app/app.nocache.js --rpc
```

Generate and test RPC requests:

```bash
python3 gwtmap.py -u https://target/app/app.nocache.js --rpc --probe
```

Enumerate GWTP Action classes:

```bash
python3 gwtmap.py -u https://target/app/app.nocache.js --actions
```

Filter methods:

```bash
python3 gwtmap.py -u https://target/app/app.nocache.js --filter AuthService
```

---

## Supported Targets

* Google Web Toolkit (GWT)
* GWT-RPC
* GWT 2.x
* GWT 2.7+
* GWT 2.8+
* GWTP (GWT Platform)
* DispatchService implementations
* Obfuscated production builds
* Deferred JavaScript fragments

---

## Credits

### Original Project

This project is based on **GWTMap**, originally created by **Oliver Simonnet (@FSecureLabs)** and released by **F-Secure Labs** under the BSD 3-Clause License.

### Extended Version

Additional development, modern GWT support, GWTP Dispatch analysis, ServiceHelper support, RPC reconstruction improvements, and ongoing maintenance:

**Zero-Defense Labs**
**Jacob Hazak**

---

## License

This project retains the original **BSD 3-Clause License** from the upstream GWTMap project. Any modifications are provided under the same license unless otherwise stated.

Please retain attribution to the original author and contributors.
