FROM node:16
WORKDIR /usr/src/frontend
COPY . ./

#RUN sed -i 's/localhost:8000/backend:8000/g' src/*Api.js && \
#    sed -i 's/localhost:8000/backend:8000/g' src/*API.js
RUN npm install && npm run build && npm install -g serve

ENTRYPOINT serve -s build