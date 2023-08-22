## 第一个构建阶段：构建前端项目
##使用Node.js的LTS版本作为基础镜像，并将其命名为
#FROM node:lts AS builderxx
##设置工作目录为
#WORKDIR /app
##将前端项目的所有文件复制到容器中的/app目录。
#COPY .. /app
##安装依赖项
#RUN npm install
##构建前端项目
#RUN npm run build
#
## 第二个构建阶段：生产环境镜像
##使用Nginx的alpine版本作为基础镜像
#FROM nginx:alpine
##复制构建好的前端文件到Nginx的默认目录
#COPY --from=builder /app/dist /usr/share/nginx/html
#EXPOSE 80
#CMD ["nginx", "-g", "daemon off;"]
# 第一个构建阶段：构建前端项目
FROM node:lts AS builder
WORKDIR /app
COPY . /app
RUN npm install
RUN npm run build

# 第二个构建阶段：生产环境镜像
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
