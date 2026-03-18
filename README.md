# DST Dedicated Server Tool

轻量单文件管理脚本：`dst_tool.sh`

支持：
- 服务器启停（`screen` 模式）
- Mod 管理（安装层与启用层）
- 季节活动开关
- 存档备份/恢复
- 外部托管模式状态识别（不接管启停）

## 文件说明

- `dst_tool.sh`: 主脚本

## 依赖

- `bash`
- `screen`（仅 `screen` 模式启停需要）
- `steamcmd`（更新游戏与下载 Mod 需要）

## 下载方式

仓库地址：`https://github.com/JIE77777/Wagstaff-DSTTool`


### 方式 1：wget 下载单文件脚本

```bash
wget -O dst_tool.sh https://raw.githubusercontent.com/JIE77777/Wagstaff-DSTTool/main/dst_tool.sh
```

### 方式 2：curl 下载单文件脚本

```bash
curl -fsSL https://raw.githubusercontent.com/JIE77777/Wagstaff-DSTTool/main/dst_tool.sh -o dst_tool.sh
```

### 方式 3：Git 克隆仓库

```bash
git clone https://github.com/JIE77777/Wagstaff-DSTTool.git
cd Wagstaff-DSTTool
```

## 部署方式

### 方式 1：直接部署（推荐）

```bash
chmod +x dst_tool.sh
./dst_tool.sh --init
./dst_tool.sh
```

`--init` 会自动扫描目录并把配置写回脚本顶部 `CFG_*` 区块。

### 方式 2：外部托管（systemd/supervisor/docker/其他）

如果你的进程由外部托管，不希望脚本接管启停：

1. 运行 `./dst_tool.sh --init`
2. 确认 `CFG_SERVICE_MODE="external"`
3. 正常运行 `./dst_tool.sh`

此模式下脚本仍可用：
- Mod 管理
- 活动配置
- 日志查看
- 备份/恢复（恢复前需先停外部服务）

### 方式 3：screen 托管

如果你希望脚本接管启停：

1. 运行 `./dst_tool.sh --init`
2. 将 `CFG_SERVICE_MODE` 设为 `screen`
3. 使用主菜单 `启动/停止/重启`

## 配置说明（最小手动配置）

脚本顶部 `CFG_*` 里通常只需关心这 4 项：

- `CFG_DST_DIR`: DST 专用服目录（包含 `bin/`）
- `CFG_KLEI_DIR`: Klei 数据目录
- `CFG_SAVE_DIR_NAME`: 集群名（存档目录名）
- `CFG_SERVICE_MODE`: `screen` 或 `external`

## 常用命令

```bash
./dst_tool.sh --help   # 查看内置说明
./dst_tool.sh --init   # 初始化/重扫配置
./dst_tool.sh          # 进入交互菜单
```

## 注意事项

- 回档会覆盖当前存档目录，请谨慎操作。
- `external` 模式下，启停请使用你自己的托管系统。
- 若状态识别异常，先确认 `CFG_SAVE_DIR_NAME` 是否与实际启动参数 `-cluster` 一致。

### 主界面
<img width="931" height="558" alt="image" src="https://github.com/user-attachments/assets/27dc8606-b18a-4d9e-9901-df6d2e2a6f88" />

### 内置控制台
<img width="912" height="362" alt="image" src="https://github.com/user-attachments/assets/704da190-b081-4a60-966a-b592bdf5f9e4" />

### mod管理
<img width="624" height="320" alt="image" src="https://github.com/user-attachments/assets/b9a74485-e0a4-43d5-9289-ea9f4b4dcdd7" />

### 活动控制
<img width="796" height="682" alt="image" src="https://github.com/user-attachments/assets/c718318a-e6e8-4e80-91d4-134fe5914a25" />

### 自动扫描配置
<img width="625" height="274" alt="image" src="https://github.com/user-attachments/assets/39ed8626-901e-4f96-bf44-a4d01a7185e2" />





