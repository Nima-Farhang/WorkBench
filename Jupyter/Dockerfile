FROM python as PY
ENV PYTHONBUFFERED=1
# General Update
RUN apt-get update &&\
    apt-get install -y alien

# Installing Oracle odbc,  PYODBC, java and git
RUN apt-get install -y unixodbc-dev &&\
    wget https://download.oracle.com/otn_software/linux/instantclient/216000//oracle-instantclient-basic-21.6.0.0.0-1.el8.x86_64.rpm &&\
    wget https://download.oracle.com/otn_software/linux/instantclient/216000//oracle-instantclient-jdbc-21.6.0.0.0-1.el8.x86_64.rpm &&\
    wget https://download.oracle.com/otn_software/linux/instantclient/216000//oracle-instantclient-odbc-21.6.0.0.0-1.el8.x86_64.rpm &&\
    wget https://download.oracle.com/otn_software/linux/instantclient/216000//oracle-instantclient-sqlplus-21.6.0.0.0-1.el8.x86_64.rpm &&\
    wget https://download.oracle.com/otn_software/linux/instantclient/216000//oracle-instantclient-devel-21.6.0.0.0-1.el8.x86_64.rpm &&\        
    alien -i --scripts oracle-instantclient*.rpm &&\
    rm -f oracle-instantclient*.rpm &&\
    apt-get install -y libaio1 alien &&\
    apt-get install -y default-jre

WORKDIR /usr/src/app
# Installing python packages
COPY requirements.txt ./
RUN python3 -m pip install --upgrade pip &&\
    pip install -r requirements.txt