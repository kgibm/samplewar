# samplewar

Example usage from Docker:

`docker run --rm openliberty/open-liberty:full-java8-ibmjava-ubi sh -c "curl https://raw.githubusercontent.com/kgibm/samplewar/main/samplewar.war -so /config/dropins/sample.war && echo '<?xml version=\"1.0\" encoding=\"UTF-8\"?><server><httpEndpoint id=\"defaultHttpEndpoint\" host=\"*\" httpPort=\"9080\" httpsPort=\"9443\"><accessLogging filepath=\"\${server.output.dir}/logs/access.log\" logFormat=\"%h %u %t &quot;%r&quot; %s %b %D %{R}W\" /></httpEndpoint></server>' > /config/configDropins/overrides/server.xml && (/opt/ol/wlp/bin/server run defaultServer &) && sleep 2 && tail -99999f /logs/messages.log | grep -q CWWKF0011I && curl -sv --trace-time http://localhost:9080/sample/servlet && cat /opt/ol/wlp/output/defaultServer/logs/access.log && /opt/ol/wlp/bin/server stop defaultServer"`
