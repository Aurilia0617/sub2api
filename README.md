# 镜像构建命令

本次成功使用的镜像构建与推送命令：

```bash
VERSION=$(tr -d '\r\n' < backend/cmd/server/VERSION) && COMMIT=$(git rev-parse --short HEAD) && DATE=$(date -u +%Y-%m-%dT%H:%M:%SZ) && HTTP_PROXY=http://127.0.0.1:7897 HTTPS_PROXY=http://127.0.0.1:7897 http_proxy=http://127.0.0.1:7897 https_proxy=http://127.0.0.1:7897 docker buildx build --network host --platform linux/amd64 --build-arg HTTP_PROXY=http://127.0.0.1:7897 --build-arg HTTPS_PROXY=http://127.0.0.1:7897 --build-arg http_proxy=http://127.0.0.1:7897 --build-arg https_proxy=http://127.0.0.1:7897 --build-arg VERSION="$VERSION" --build-arg COMMIT="$COMMIT" --build-arg DATE="$DATE" --build-arg GOPROXY=https://goproxy.cn,direct --build-arg GOSUMDB=sum.golang.google.cn -t ghcr.io/aurilia0617/sub2api:latest -t ghcr.io/aurilia0617/sub2api:"$VERSION" --push .
```
