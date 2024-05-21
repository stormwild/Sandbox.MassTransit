# MassTransit Pub Sub

Sample code for article

[Integrating MassTransit using AWS SNS/SQS into your ASP.NET project](https://www.dateo-software.de/blog/integrating-masstransit)

Run docker

```sh
cd Messaging.Core/
docker compose up -d
```

Verify services are running

```sh
docker ps --format "table {{.Names}}\t{{.ID}}\t{{.Command}}\t{{.Status}}\t{{.Ports}}"
```

Outputs

```sh
NAMES             CONTAINER ID   COMMAND                  STATUS                        PORTS
localstack_main   7432568adbe7   "docker-entrypoint.sh"   Up About a minute (healthy)   127.0.0.1:4510-4559->4510-4559/tcp, 127.0.0.1:4566->4566/tcp, 5678/tcp
```

Run Producer

```sh
cd WebApi.Producer/
dotnet run
```

Run Consumer

```sh
cd WebApi.Consumer/
dotnet run
```

View Terminal for Producer

```sh
Building...
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:5135
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: /workspaces/Sandbox.MassTransit/WebApi.Producer
info: MassTransit[0]
      Bus started: amazonsqs://localhost/
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:25:43 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:25:48 +00:00
info: WebApi.Producer.AgeRequestHandler[0]
      Sending age request
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:25:51 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:25:54 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:25:57 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:00 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:03 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:06 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:09 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:12 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:15 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:18 +00:00
warn: WebApi.Producer.AgeRequestHandler[0]
      No one responded
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:21 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:24 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:27 +00:00
info: WebApi.Producer.HeartBeatSender[0]
      Sent heartbeat 05/21/2024 07:26:30 +00:00
info: WebApi.Producer.AgeRequestHandler[0]
      Sending age request
info: WebApi.Producer.AgeRequestHandler[0]
      Received age response 00:37:36.3130000
```

View Terminal for Consumer

```sh
Building...
info: MassTransit[0]
      Configured endpoint HeartBeat, Consumer: WebApi.Consumer.HeartBeatConsumer
info: MassTransit[0]
      Configured endpoint TellMeYourAge.fifo, Consumer: WebApi.Consumer.TellMeYourAgeConsumer
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:5195
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: /workspaces/Sandbox.MassTransit/WebApi.Consumer
info: MassTransit[0]
      Bus started: amazonsqs://localhost/
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 8b07159a-94aa-4201-9551-efc321a87b8e and timestamp 05/21/2024 07:25:57 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 7c99b877-a1b7-452d-8b39-b957cb1a5f0a and timestamp 05/21/2024 07:26:00 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 5372506d-e1a3-41fb-9c73-7b6e5cc272b7 and timestamp 05/21/2024 07:26:03 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 9af06d23-0da8-400a-8d5f-2a03f64ec261 and timestamp 05/21/2024 07:26:06 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID e98f9d9a-da86-438c-8dfc-a11f36910ad8 and timestamp 05/21/2024 07:26:09 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 5d6507a1-751a-4600-ab79-3b0ee3fd131c and timestamp 05/21/2024 07:26:12 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 9c8b2091-1190-411e-b11a-efaf58812be4 and timestamp 05/21/2024 07:26:15 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 9a964be4-2268-4c6a-8d5c-52c6d9d23e52 and timestamp 05/21/2024 07:26:18 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 4f2a7eb7-c1fd-47ef-b63e-9c3809828c5a and timestamp 05/21/2024 07:26:21 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID c360d670-0ee1-4c30-a9bf-72d281f14c11 and timestamp 05/21/2024 07:26:24 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID b816804e-a8a4-44fb-91b5-2e849ea9164b and timestamp 05/21/2024 07:26:27 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 981ad4a4-8c74-41b3-93ad-ab0fef316965 and timestamp 05/21/2024 07:26:30 +00:00
info: WebApi.Consumer.TellMeYourAgeConsumer[0]
      Received age request
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 9b29dd8a-64de-4b0b-83c0-d0b52141589e and timestamp 05/21/2024 07:26:33 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID afd4eebf-cdb9-4489-8790-a3e40ab84ba3 and timestamp 05/21/2024 07:26:36 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 29b69433-20c4-4eab-bfc3-0c4625a38fc4 and timestamp 05/21/2024 07:26:39 +00:00
info: WebApi.Consumer.TellMeYourAgeConsumer[0]
      Received age request
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID e1e8ac9d-4a08-4725-a0f9-26c8c282a520 and timestamp 05/21/2024 07:26:42 +00:00
info: WebApi.Consumer.HeartBeatConsumer[0]
      Received heartbeat with ID 5f2cd35f-bbc5-4209-bcf6-8fc2ff959201 and timestamp 05/21/2024 07:26:45 +00:00
```

Note that the producer sends a request for age but there is not consumer to receive and respond to the request.

```sh
info: WebApi.Producer.AgeRequestHandler[0]
      Sending age request

warn: WebApi.Producer.AgeRequestHandler[0]
      No one responded

info: WebApi.Producer.AgeRequestHandler[0]
      Sending age request
info: WebApi.Producer.AgeRequestHandler[0]
      Received age response 00:37:36.3130000      
```

```sh
info: WebApi.Consumer.TellMeYourAgeConsumer[0]
      Received age request
```

It was only when the consumer api/service was started that it was able to respond to the request.
