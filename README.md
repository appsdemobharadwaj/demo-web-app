      name: "Deploy Mesos Application  "
      register: docker
    - 
      command: "ant war"
    - 
      command: "docker build --no-cache --tag bharadwajsnp/mckinsey-sp:latest ."
    - 
      command: "docker login -u bharadwajsnp -p Webhosting123"
    - 
      command: "docker push bharadwajsnp/mckinsey-sp:latest"
    - 
      command: "ansible-playbook ansible-login-mesos.yml"
	- 
      command: "ansible-playbook ansible-sp-mesos.yml"
    - 
      debug: var=docker.stdout
