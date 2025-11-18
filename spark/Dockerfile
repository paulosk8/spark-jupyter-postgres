FROM apache/spark:4.0.1-scala2.13-java21-python3-ubuntu

# Cambiar a usuario root para instalar paquetes
USER root

# Instala Python y Jupyter
RUN apt-get update && \
    apt-get install -y python3-pip wget unzip libpq-dev && \
    pip3 install --upgrade pip && \
    pip3 install jupyter pyspark pandas matplotlib seaborn psycopg2-binary

# Descarga el driver JDBC para PostgreSQL
RUN wget https://jdbc.postgresql.org/download/postgresql-42.7.1.jar -P /opt/spark/jars/

# Crea carpeta de trabajo
WORKDIR /home/jovyan/work

# Generar configuración de Jupyter y deshabilitar token
RUN jupyter notebook --generate-config && \
    echo "c.NotebookApp.token = ''" >> /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.password = ''" >> /root/.jupyter/jupyter_notebook_config.py

EXPOSE 8888 4040
