# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 

```
import socket
import webbrowser
import os
import threading


def start_server():

    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    server.bind(("127.0.0.1", 8080))

    server.listen(1)

    print("Server running on port 8080...")

    conn, addr = server.accept()

    print("Connected by:", addr)

    request = conn.recv(1024).decode()

    print("Request received:\n")
    print(request)

    html_content = """
    <html>

    <head>
        <title>CN Lab Webpage</title>
    </head>

    <body style="
        background-color: lightblue;
        text-align: center;
        font-family: Arial;">

        <h1 style="color: green;">
            Welcome to My Webpage 
        </h1>

        <h2 style="color: red;">
            Mithun Kumar [212225040236]
        </h2>

        <button style="
            background-color: blue;
            color: white;
            font-size: 20px;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;">

            Click Me

        </button>

    </body>

    </html>
    """

    response = (
        "HTTP/1.1 200 OK\r\n"
        "Content-Type: text/html\r\n\r\n"
        + html_content
    )

    conn.sendall(response.encode())

    conn.close()

    server.close()


def open_browser():

    webbrowser.open("http://127.0.0.1:8080")


server_thread = threading.Thread(target=start_server)

server_thread.start()

open_browser()
```
## OUTPUT
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/63d7d62d-cebb-45cf-98b0-88a0a2e7a0d7" />


## Result
Thus the socket for HTTP for web page upload and download created and Executed
