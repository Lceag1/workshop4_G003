# Imagen base ligera
FROM python:3.11-slim

# Instalar dependencias necesarias
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*

# Directorio de trabajo
WORKDIR /app

# Copiar solo requirements primero para aprovechar caché
COPY src/requirements.txt /app/src/requirements.txt

# Instalar uv y dependencias
RUN pip install --upgrade pip uv \
    && uv pip install -r /app/src/requirements.txt --system

# Copiar el resto del código
COPY . /app

# Exponer puerto
EXPOSE 5001

# Ejecutar la aplicación con uv
CMD ["uv", "run", "python", "src/app.py"]

