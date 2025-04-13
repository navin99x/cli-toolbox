# 🌐 cURL

> cURL (client URL) is a powerful command line tool used to transfer data to and from servers using various network protocols.

---

## 📥 Installation

cURL comes preinstalled on many operating systems. Check if you have it with:

```bash
curl --version
```

If not installed, run these commands on your system:

**Linux/WSL:** 🐧
```bash
sudo apt-get install curl
```

**macOS:** 🍎
```bash
brew install curl  # Using Homebrew
```

**Windows:** 🪟
```powershell
winget install --id cURL.cURL -e
```

## 🚀 Basic Syntax

```bash
curl [options] [url]
```

## Common Use Cases

### HTTP Requests

```bash
# GET Request 🔍
curl https://httpbin.org/get

# POST Request 📬
curl -X POST -d "username=ben&password=1234" https://httpbin.org/post

# POST with JSON data
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"username":"ben","password":"1234"}' \
  https://httpbin.org/post
```

### Other HTTP Methods 🔄
```bash
# PUT request
curl -X PUT -d "data=updated" https://httpbin.org/put

# DELETE request
curl -X DELETE https://httpbin.org/delete

# PATCH request
curl -X PATCH -d "data=partial" https://httpbin.org/patch
```

### 💾 File Operations

```bash
# Save with original filename
curl -O https://example.com/file.zip 

# Save with custom name
curl -o download.zip https://example.com/file.zip

# Upload file using POST
curl -F "file=@localfile.txt" https://httpbin.org/post

# Upload using PUT
curl -T localfile.txt https://httpbin.org/put
```

### 🔐 Authentication

```bash
# Basic Authentication 🔑
curl -u ben:1234 https://httpbin.org/basic-auth/ben/1234

# Bearer Token 🪙
curl -H "Authorization: Bearer A1B2" https://httpbin.org/bearer
```

### 📋 Header Information

#### Verbose Mode 🔍
```bash
# Show detailed connection info (> for request, < for response)
curl -v https://httpbin.org
```

#### Header Only 📝
```bash
# Show response headers only
curl -I https://www.httpbin.org
```

#### Response with Headers 📄
```bash
# Show both headers and response body
curl -i https://www.httpbin.org
```

#### Custom Headers 🎭
```bash
# Add custom headers
curl -H "User-Agent: MyCurlClient/1.0" -H "Accept-Language: en-US" https://httpbin.org/headers
```

### 🚦 Traffic Control

#### Follow Redirects 🔀
```bash
# Follow up to 5 redirects
curl -L https://httpbin.org/redirect/5
```

#### Rate Limiting ⏱️
```bash
# Limit download speed (bytes per second)
curl --limit-rate 100K https://example.com/large-file.zip
```

#### Connection Timeouts ⏳
```bash
# Connection timeout in seconds
curl --connect-timeout 5 https://example.com

# Total operation timeout
curl --max-time 10 https://httpbin.org/delay/9
```

### 🍪 Cookie Management

#### Send Cookies 🍪
```bash
curl --cookie "name=ben; age=20" https://httpbin.org/cookies
```

#### Save Cookies 📝
```bash
curl -c cookies.txt https://httpbin.org/cookies/set/name/ben
```

#### Load and Save Cookies 🔄
```bash
curl -b cookies.txt -c cookies.txt https://httpbin.org/cookies
```

### 🧩 Additional commands

#### Silent Mode 🤫
```bash
# Hide progress meter and error messages
curl -s https://httpbin.org/get
```

#### Show Progress Bar 📊
```bash
# Display progress bar during download
curl -# -O https://example.com/large-file.zip
```

#### Proxy Usage 🔄
```bash
# Use a proxy server
curl -x http://proxy-server:port https://httpbin.org/ip
```

### 📺 Output Control

#### Save Output to File 💾
```bash
# Save response to file
curl https://example.com > output.html
```

#### Suppress Output 🔇
```bash
# Don't show response on screen
curl -o /dev/null https://example.com
```

#### Detailed Timing Stats 📊
```bash
curl -w "\nDNS: %{time_namelookup}s\nConnect: %{time_connect}s\nTLS: %{time_appconnect}s\nTotal: %{time_total}s\n" -o /dev/null https://example.com
```

## 💡 My Use Cases

- 🔎 API testing and debugging
- 📊 Fetching and processing JSON data with jq
- 📊 Performance testing of endpoints

## 📚 Resources

- 📘 [cURL Command Manual](https://curl.se/docs/manpage.html)
- 🧠 [Everything cURL - Free eBook](https://everything.curl.dev/)
- 📝 [Linux Handbook cURL Guide](https://linuxhandbook.com/curl-command-examples/)
- 🛠️ [cURL Cookbook](https://catonmat.net/cookbooks/curl)
