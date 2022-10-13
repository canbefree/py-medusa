FROM python:3.9-bullseye as build 

RUN pip install --upgrade pip
RUN pip install numpy && \
    pip install jupyter && \
    pip install pandas && \
    pip install matplotlib

RUN jupyter notebook --generate-config
COPY jupyter_notebook_config.json ~/.jupyter/jupyter_notebook_config.json
RUN sed -i "s/# c.NotebookApp.token = '<generated>'/c.NotebookApp.token = ''/" ~/.jupyter/jupyter_notebook_config.py

FROM build as development
CMD ["jupyter","notebook"]