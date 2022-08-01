FROM node:14.17-alpine

ENV TZ Asia/Tokyo

#ローカル開発用（docker compose対応）
#COPY docker/front/frontend /usr/src/app

#デプロイ用
COPY ./frontend /usr/src/app

WORKDIR /usr/src/app

#COPY ./frontend/.next /usr/src/app

RUN npm install 
#RUN apk update
#RUN npm run build
#ENV PATH $HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH

EXPOSE 3000

ENTRYPOINT ["npm", "run", "dev"]