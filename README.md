## PGN Chess Server

PHP Ratchet WebSocket chess server.

### Set Up

Create an `.env` file:

    cp .env.example .env

Bootstrap the environment:

    bash/dev/start.sh

Find out your Docker container's IP address:

    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' pgn_chess_server_php_fpm

### WebSocket Server

Start the server:

    docker exec -it --user 1000:1000 pgn_chess_server_php_fpm php cli/ws-server.php

Open a console in your favorite browser and play PGN moves:

    const ws = new WebSocket('ws://172.23.0.2:8080');
    ws.onmessage = (res) => { console.log(res.data) };
    ws.send('w e4');
    ws.send('b e5');

### Telnet Server

Start the server:

    docker exec -it --user 1000:1000 pgn_chess_server_php_fpm php cli/t-server.php

Open a command prompt and play PGN moves:

    telnet 172.23.0.2 8080
    w e4
    b e5

### License

The MIT License (MIT) Jordi Bassagañas.

### Contributions

Would you help make this app better?

- Feel free to send a pull request
- Drop an email at info@programarivm.com with the subject "PGN Chess Server"
- Leave me a comment on [Twitter](https://twitter.com/programarivm)

Thank you.
