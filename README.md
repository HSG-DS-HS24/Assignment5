# Fault-Tolerant Key/Value Service


## Project Structure

```bash
bin #A folder to put your scripts (.bat for Windows or .sh for macOS and Linux)
└── partition #A folder for the scripts related to the network partition
images #A folder where to put the screenshots that you generate.
kv #A folder where to implement the key/value service
└── kvstorage.py #A Python script to implement an instance of the Key/Value Service.
└── kvstorage_http.py #A Python script to implement an HTTP server to interact with an instance of the Key/Value Service.
api_description.yml #The API description of the server to implement
README.md #This README.
Report.md #The Report to complete
```

## Initialization

The Python Library PySyncObj (https://readthedocs.org/projects/pysyncobj/) will be used through the Assignment.

The library can be installed with:
```bash
pip install pysyncobj
```

Note: Python 3 should be used for this Assignment. If your command python is not for Python 3, please update it (or use python3 instead).

## Task 1: Discovering Raft

The website https://raft.github.io/ shows an interactive visualization of how Raft works for
a group of 5 servers, supporting a simple database with only one type of transaction.

Answer the questions about it in your Report.

## Task 2: Implementation of a Fault-Tolerant Key/Value Service with Raft

In this task, you should complete the Python scripts [`kvstorage.py`](kv/kvstorage.py)  and [`kvtosrage_http.py`](kv/kvstorage_http.py), in the kv folder.

[`kvstorage.py`](kv/kvstorage.py)  is an implementation of a Raft server, implementing a key/value store. 

[`kvtosrage_http.py`](kv/kvstorage_http.py) is an HTTP server that enables interactions with a Raft server from kvstorage.py.

The script [`kvstorage.py`](kv/kvstorage.py)  takes the following parameters:

- The port for the HTTP server (e.g., 8080).
- The address of the Raft node (e.g., 127.0.0.1:6000)
- The next parameters are the addresses of the other Raft nodes (e.g., 127.0.0.1:6001)

To start the servers, use the scripts provided in the [`bin`](bin) folder. These scripts should be run from the bin folder in different terminals.


On Windows

```bash
.\create_server0.bat #And the other numbers
```

On macOS and Linux

```bash
chmod +x create_server0.sh #And the other numbers
./create_server0.sh #And the other numbers
```

The API description for the HTTP servers is provided in [`api_description.yml`](api_description.yml)

You can perform a PUT operation to the key/value service for key "a" with: 

POST https://localhost:8080/keys/a HTTP/1.1
Content-Type: application/json

{"type": "PUT",
"value": ["cat", "dog"]
}

You can perform an APPEND operation to the key/value service for key "a" with: 

POST https://localhost:8080/keys/a HTTP/1.1
Content-Type: application/json

{"type": "APPEND",
"value": "mouse"
}

You can perform a GET operation to the key/value service for key "a" with:

GET https://localhost:8080/keys/a HTTP/1.1

You can also perform this operation to another node to see that it has been replicated with (for example):

GET https://localhost:8081/keys/a HTTP/1.1

You can retrieve the status of node 0 with:

GET https://localhost:8080/admin/status HTTP/1.1

Complete Task 2 in the Report


# Task 3: Evaluation of the Key/Value Service

Complete Task 3 in the Report.

## Network partition

This task requires two computers. Three servers (0,1, and 2) are run on the first computer and two servers (3 and 4) are run on the second computer.

The two computers should be in the same local network. 

### Determine the IP addresses of each machine

On Windows and macOS: 

```bash
ipconfig
```

On Linux: 

```bash
ip a
```

An IPv4 address has the form A.B.C.D The two IP addresses should have the same A, B and C since they are in the same local network.

The two IP addresses will be referred to as IP1 and IP2.

The machine with IP1 should run the servers 0, 1, and 2 while the machine with IP2 should run servers 3 and 4.

Each server is run on its own machine with:

On Windows (in folder [`bin/partition`](bin/partition): 

```bash
.\create_server_partition0.bat %IP1 %IP2 #And the other numbers
```

On Linux and macOS (in folder [`bin/partition`](bin/partition): 

```bash
chmod +x create_server_partition0.sh #And the other numbers
./create_server_partition0.sh $IP1 $IP2 #And the other numbers
```

Note: 

You need to make the ports available to external computer.

You can do so on Linux with (as superuser):

```bash
ufw allow $PORT
```

You can do so on Windows with (as administrator in Powershell): 

```bash
netsh advfirewall firewall add rule name= "Open Port 80" dir=in action=allow protocol=TCP localport=80
```

You can do so on macOS with (as superuser):

1. Open /etc/pf.conf.
2. Add a line: 
 ```bash
pass in proto tcp from any to any port $PORT
```

# Task 4: Questions on Raft

Answer the questions in the Report.