# CTY Files Mirror / CTY 文件镜像

[English](#english) | [中文](#中文)

---

## English

### Overview

This repository provides mirrored copies of amateur radio CTY database files with reliable access for users in China and other regions with network restrictions.

### What's Included

- **cty.plist**: Country data in XML plist format (from country-files.com/cty/)
- **cty.dat**: Extended country data in DAT format (from country-files.com/bigcty/)
- **update_info.json**: Metadata containing file sizes, update timestamps, and mirror URLs

### Download URLs

#### Primary (CDN Accelerated)
```
https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.plist
https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.dat  
https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/update_info.json
```

#### Alternative Mirrors
```
https://ghproxy.com/https://raw.githubusercontent.com/tyler4096/cty-mirror/main/cty.plist
https://kgithub.com/tyler4096/cty-mirror/raw/main/cty.plist
https://raw.fastgit.org/tyler4096/cty-mirror/main/cty.plist
```

### Usage in Your Application

#### Check for Updates
```python
import requests
import json
from datetime import datetime

def check_updates(local_timestamp):
    """Check if newer files are available"""
    try:
        info_url = "https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/update_info.json"
        response = requests.get(info_url, timeout=10)
        remote_info = response.json()
        
        remote_time = datetime.fromisoformat(remote_info["last_updated"].replace('Z', '+00:00'))
        local_time = datetime.fromisoformat(local_timestamp.replace('Z', '+00:00'))
        
        return remote_time > local_time, remote_info
    except Exception as e:
        print(f"Update check failed: {e}")
        return False, None
```

#### Download Files
```bash
# Download via curl
curl -fsSL "https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.plist" -o cty.plist
curl -fsSL "https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.dat" -o cty.dat
```

### Update Schedule

Files are automatically updated daily at:
- **UTC**: 02:00
- **Beijing Time**: 10:00

Manual triggers are also available via GitHub Actions.

### Source Attribution

Original files sourced from:
- https://www.country-files.com/cty/cty.plist
- https://www.country-files.com/bigcty/cty.dat

### License

The mirrored files follow the licensing terms of the original sources. This mirror service is provided for convenience and educational purposes.

---

## 中文

### 概述

本仓库提供业余无线电 CTY 数据库文件的镜像副本，为国内及其他网络受限区域的用户提供可靠访问。

### 包含文件

- **cty.plist**: XML plist 格式的国家地区数据（来自 country-files.com/cty/）
- **cty.dat**: DAT 格式的扩展国家地区数据（来自 country-files.com/bigcty/）
- **update_info.json**: 包含文件大小、更新时间戳和镜像URL的元数据文件

### 下载地址

#### 主要地址（CDN加速）
```
https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.plist
https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.dat  
https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/update_info.json
```

#### 备用镜像
```
https://ghproxy.com/https://raw.githubusercontent.com/tyler4096/cty-mirror/main/cty.plist
https://kgithub.com/tyler4096/cty-mirror/raw/main/cty.plist
https://raw.fastgit.org/tyler4096/cty-mirror/main/cty.plist
```

### 在程序中使用

#### 检查更新
```python
import requests
import json
from datetime import datetime

def check_updates(local_timestamp):
    """检查是否有新版本文件可用"""
    try:
        info_url = "https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/update_info.json"
        response = requests.get(info_url, timeout=10)
        remote_info = response.json()
        
        remote_time = datetime.fromisoformat(remote_info["last_updated"].replace('Z', '+00:00'))
        local_time = datetime.fromisoformat(local_timestamp.replace('Z', '+00:00'))
        
        return remote_time > local_time, remote_info
    except Exception as e:
        print(f"更新检查失败: {e}")
        return False, None
```

#### 下载文件
```bash
# 使用 curl 下载
curl -fsSL "https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.plist" -o cty.plist
curl -fsSL "https://cdn.jsdelivr.net/gh/tyler4096/cty-mirror@main/cty.dat" -o cty.dat
```

### 更新频率

文件自动更新计划：
- **UTC时间**: 02:00
- **北京时间**: 10:00

也可以通过 GitHub Actions 手动触发更新。

### 源文件声明

原始文件来源于：
- https://www.country-files.com/cty/cty.plist
- https://www.country-files.com/bigcty/cty.dat

### 许可证

镜像文件遵循原始源的许可条款。本镜像服务仅为了方便和教育目的而提供。

---

**73 de tyler4096**
