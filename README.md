# EFK-V2.4
To make this work on ubuntu 20.04:
    - Install td-agent:
        - curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-focal-td-agent4.sh | sh
    - Set up configuration for localhost (for remote host change an IP address in td-agent.conf in server part to IP you need):
        - Go to /path/to/EFK-V2.4(final)/fluentd/td-agent.conf
        - Copy configuration and copy in td-agent.conf whisch already exists
        - restart service using:
            - systemctl restart td-agent
    - Run dokcer-compose file
        docker-compose up -d
    
    - To make status green use template in Kibana console: 
        PUT _template/template_1
        {
            "index_patterns": ["*"],           <-- applies to all indexes
            "order": 0,                        <-- lowest priority
            "settings": {
                "number_of_shards": 1,
                "number_of_replicas": 0
            }
        }
