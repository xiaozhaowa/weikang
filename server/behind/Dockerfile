# 基于Golang的镜像作为构建镜像
FROM golang:latest AS build

# 设置工作目录
WORKDIR /app

# 复制项目文件到工作目录
COPY . .

# 构建后端项目
RUN go build -o main .

# 使用一个不含编译环境的小镜像作为生产镜像
FROM alpine:latest

# 设置工作目录
WORKDIR /app

# 从构建镜像中复制构建好的项目文件到生产镜像
COPY --from=build /app/main .

# 暴露后端应用程序的端口
EXPOSE 8888

# 定义启动后端应用程序的命令
CMD ["./main"]
