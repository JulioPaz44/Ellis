# Usa uma imagem oficial e leve do Python como imagem base
FROM python:3.13.5-alpine3.22

# Define o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copia o arquivo de dependências para o diretório de trabalho.
# Isso é feito em um passo separado para aproveitar o cache de camadas do Docker.
COPY requirements.txt .

# Instala os pacotes necessários especificados no requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copia o restante do código da aplicação para o diretório de trabalho
COPY . .

# Expõe a porta em que a aplicação será executada
EXPOSE 8000

# Define o comando para executar a aplicação em produção
# Usa --host 0.0.0.0 para torná-la acessível de fora do contêiner
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]