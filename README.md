## Gerenciamento LIBVIRT por linha de comando

### Domain Management:
1. Criar uma nova máquina virtual:
   ```
   virt-install --name myvm --memory 2048 --vcpus 2 --disk path=/var/lib/libvirt/images/myvm.qcow2,size=20 --os-type linux --os-variant ubuntu20.04 --network bridge=virbr0 --graphics none --console pty,target_type=serial --location 'http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/' --extra-args 'console=ttyS0,115200n8 serial'

   ```

2. Iniciar uma máquina virtual:
   ```
   virsh start myvm
   ```

3. Parar uma máquina virtual:
   ```
   virsh shutdown myvm
   ```

4. Reiniciar uma máquina virtual:
   ```
   virsh reboot myvm
   ```

5. Excluir uma máquina virtual:
   ```
   virsh undefine myvm
   ```

### Domain Monitoring:
1. Verificar o status de todas as máquinas virtuais:
   ```
   virsh list --all
   ```

2. Obter informações detalhadas sobre uma máquina virtual específica:
   ```
   virsh dominfo myvm
   ```

3. Monitorar o uso de CPU de uma máquina virtual:
   ```
   virsh domstats myvm
   ```

4. Monitorar o uso de memória de uma máquina virtual:
   ```
   virsh dommemstat myvm
   ```

5. Visualizar os logs de uma máquina virtual:
   ```
   journalctl -u libvirtd
   ```

### Host and Hypervisor:
1. Verificar o status do hypervisor:
   ```
   virsh nodeinfo
   ```

2. Listar os dispositivos de armazenamento disponíveis no host:
   ```
   virsh pool-list
   ```

3. Listar os dispositivos de rede disponíveis no host:
   ```
   virsh net-list
   ```

4. Verificar informações do host:
   ```
   virsh hostname
   ```

5. Desligar o host:
   ```
   virsh shutdown
   ```

### Interface:
1. Criar uma nova interface de rede:
   ```
   virsh iface-define /etc/libvirt/qemu/networks/mynetwork.xml
   ```

2. Iniciar uma interface de rede:
   ```
   virsh iface-start mynetwork
   ```

3. Parar uma interface de rede:
   ```
   virsh iface-stop mynetwork
   ```

4. Excluir uma interface de rede:
   ```
   virsh iface-undefine mynetwork
   ```

5. Listar interfaces de rede disponíveis:
   ```
   virsh iface-list
   ```

### Network Filter:
1. Criar um filtro de rede:
   ```
   virsh nwfilter-define /etc/libvirt/nwfilter/mynwfilter.xml
   ```

2. Aplicar um filtro de rede a uma interface:
   ```
   virsh attach-interface --domain myvm --type network --source mynetwork --model virtio --config
   ```

3. Remover um filtro de rede de uma interface:
   ```
   virsh detach-interface --domain myvm --type network --mac 52:54:00:00:00:01 --config
   ```

4. Listar filtros de rede disponíveis:
   ```
   virsh nwfilter-list
   ```

5. Excluir um filtro de rede:
   ```
   virsh nwfilter-undefine mynwfilter
   ```

### Networking:
1. Criar uma nova rede:
   ```
   virsh net-define /etc/libvirt/qemu/networks/mynetwork.xml
   ```

2. Iniciar uma rede:
   ```
   virsh net-start mynetwork
   ```

3. Parar uma rede:
   ```
   virsh net-destroy mynetwork
   ```

4. Excluir uma rede:
   ```
   virsh net-undefine mynetwork
   ```

5. Listar redes disponíveis:
   ```
   virsh net-list
   ```

### Snapshot:
1. Criar um snapshot de uma máquina virtual:
   ```
   virsh snapshot-create-as myvm snapshot1 "Descrição do snapshot"
   ```

2. Listar snapshots de uma máquina virtual:
   ```
   virsh snapshot-list myvm
   ```

3. Reverter para um snapshot específico:
   ```
   virsh snapshot-revert myvm snapshot1
   ```

4. Excluir um snapshot de uma máquina virtual:
   ```
   virsh snapshot-delete myvm snapshot1
   ```

5. Criar um snapshot e excluir instantaneamente os antigos:
   ```
   virsh snapshot-create-as --atomic myvm snapshot2 "Descrição do snapshot"
   ```

### Storage Pool:
1. Criar um novo pool de armazenamento:
   ```
   virsh pool-define-as mypool dir --target /var/lib/libvirt/images
   ```

2. Iniciar um pool de armazenamento:
   ```
   virsh pool-start mypool
   ```

3. Parar um pool de armazenamento:
   ```
   virsh pool-stop mypool
   ```

4. Excluir um pool de armazenamento:
   ```
   virsh pool-destroy mypool
   virsh pool-undefine mypool
   ```

5. Listar pools de armazenamento disponíveis:
   ```
   virsh pool-list
   ```

### Storage Volume:
1. Criar um novo volume de armazenamento:
   ```
   virsh vol-create-as mypool myvolume.qcow2 10G
   ```

2. Listar volumes de armazenamento em um pool:
   ```
   virsh vol-list mypool
   ```

3. Excluir um volume de armazenamento de um pool:
   ```
   virsh vol-delete mypool myvolume.qcow2
   ```

4. Redimensionar um volume de armazenamento:
   ```
   virsh vol-resize mypool myvolume.qcow2 20G
   ```

5. Clonar um volume de armazenamento:
   ```
   virsh vol-clone --pool mypool myvolume.qcow2 myclonedvolume.qcow2
   ```
