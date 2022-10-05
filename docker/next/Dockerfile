
FROM node:16-alpine AS development
WORKDIR /app

ENV NODE_ENV development

EXPOSE 3000
ENV PORT 3000
CMD ["yarn", "dev"]

FROM node:16-alpine AS production
WORKDIR /app

ENV NODE_ENV production

RUN addgroup --system --gid 1001 nextjs_frontend
RUN adduser --system --uid 1001 nextjs_frontend

COPY . .

RUN yarn install

RUN yarn build

RUN chown nextjs_frontend:nextjs_frontend /app/.next/

USER nextjs_frontend

EXPOSE 3000

ENV PORT 3000

CMD ["yarn", "start"]
