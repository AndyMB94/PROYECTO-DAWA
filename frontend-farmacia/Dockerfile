# Etapa de construcción
FROM node:18-alpine AS builder

WORKDIR /app

# Copiar package.json y package-lock.json
COPY package*.json ./

# Instalar dependencias
RUN npm ci

# Copiar código fuente
COPY . .

# Construir la aplicación
RUN npm run build

# Etapa de producción
FROM node:18-alpine AS runner

WORKDIR /app

# Crear usuario no root
RUN addgroup --system --gid 1001 nodejs
RUN adduser --system --uid 1001 nextjs

# Copiar archivos necesarios
COPY --from=builder /app/public ./public
COPY --from=builder /app/.next/standalone ./
COPY --from=builder /app/.next/static ./.next/static

# Cambiar propietario de archivos
RUN chown -R nextjs:nodejs /app

USER nextjs

# Exponer puerto
EXPOSE 3000

# Variables de entorno
ENV PORT 3000
ENV HOSTNAME "0.0.0.0"

# Comando para ejecutar
CMD ["node", "server.js"]