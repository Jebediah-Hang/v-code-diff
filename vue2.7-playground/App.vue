<script lang="ts" setup>
import { onMounted, reactive, ref } from 'vue'

const form = reactive({
  oldString: '#\n version 7.1.071, Release 6343P08\n#\n sysname JR-RZQ2-GJKXCTCGD-S5130-03\n#\n clock timezone Beijing add 08:00:00\n#\n telnet server enable\n#\n irf mac-address persistent timer\n irf auto-update enable\n undo irf link-delay\n irf member 1 priority 1\n#\n dot1x\n dot1x authentication-method eap\n#\n lldp compliance cdp\n lldp global enable\n#\n password-recovery enable\n#\nvlan 1\n#\nvlan 10\n#\nvlan 42 to 43\n#\nvlan 50\n#\nvlan 52\n#\nvlan 54\n#\nvlan 57\n#\nvlan 59\n#\n stp mode pvst\n stp pathcost-standard dot1t\n stp global enable\n#\ninterface NULL0\n#\ninterface Vlan-interface1\n ip address 10.99.51.59 255.255.255.128\n#\ninterface GigabitEthernet1/0/1\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n lldp compliance admin-status cdp txrx\n#\ninterface GigabitEthernet1/0/2\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n lldp compliance admin-status cdp txrx\n#\ninterface GigabitEthernet1/0/3\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/4\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/5\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/6\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/7\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/8\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/9\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/10\n port link-type trunk\n port trunk permit vlan all\n stp edged-port\n lldp compliance admin-status cdp txrx\n#\ninterface GigabitEthernet1/0/11\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/12\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/13\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/14\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/15\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/16\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/17\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/18\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/19\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/20\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/21\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/22\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/23\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/24\n port access vlan 52\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n#\ninterface GigabitEthernet1/0/25\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n#\ninterface GigabitEthernet1/0/26\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n#\ninterface GigabitEthernet1/0/27\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n#\ninterface GigabitEthernet1/0/28\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n#\n scheduler logfile size 16\n#\nline class aux\n user-role network-admin\n#\nline class vty\n user-role network-operator\n#\nline aux 0\n authentication-mode scheme\n user-role network-admin\n#\nline vty 0 4\n authentication-mode scheme\n user-role network-admin\n user-role network-operator\n#\nline vty 5 63\n user-role network-operator\n#\n ip route-static 0.0.0.0 0 10.99.51.1\n#\n info-center loghost source Vlan-interface1\n info-center loghost 10.99.160.43\n info-center loghost 10.99.216.202\n info-center loghost 10.188.19.194\n#\n snmp-agent\n snmp-agent local-engineid 800063A280AC740990441B00000001\n snmp-agent community read cisco123\n snmp-agent sys-info version all \n#\n ifmonitor crc-error slot 1 high-threshold 1000 low-threshold 100 interval 30\n ifmonitor input-error slot 1 high-threshold 1000 low-threshold 100 interval 30\n ifmonitor output-error slot 1 high-threshold 1000 low-threshold 100 interval 30\n#\n ssh server enable\n#\n ntp-service enable\n ntp-service unicast-server 10.188.16.101\n#\nradius scheme aaa\n primary authentication 10.88.250.11 key cipher $c$3$W7oDYMVFPBizP6DxRSSTnJgmfgxQrjkwFw==\n secondary authentication 10.88.250.12 key cipher $c$3$LxXs0oaYAOibpziuPCnw57r27CmZQDyLtA==\n#\nradius scheme system\n user-name-format without-domain\n#\ndomain system\n authentication login local\n authorization login local\n authentication default radius-scheme aaa\n authorization default radius-scheme aaa\n#\n domain default enable system\n#\nrole name level-0\n description Predefined level-0 role\n#\nrole name level-1\n description Predefined level-1 role\n#\nrole name level-2\n description Predefined level-2 role\n#\nrole name level-3\n description Predefined level-3 role\n#\nrole name level-4\n description Predefined level-4 role\n#\nrole name level-5\n description Predefined level-5 role\n#\nrole name level-6\n description Predefined level-6 role\n#\nrole name level-7\n description Predefined level-7 role\n#\nrole name level-8\n description Predefined level-8 role\n#\nrole name level-9\n description Predefined level-9 role\n#\nrole name level-10\n description Predefined level-10 role\n#\nrole name level-11\n description Predefined level-11 role\n#\nrole name level-12\n description Predefined level-12 role\n#\nrole name level-13\n description Predefined level-13 role\n#\nrole name level-14\n description Predefined level-14 role\n#\nuser-group system\n#\nlocal-user admin class manage\n password hash $h$6$/C7/3fVpcHEVVXlC$ot47SNj6EplhG+ROKe4RC9Kh4sgrgSyaATnc6Nh5OyyKdb5Ay9o1QqpFqBjAWGPASkof6g1sS7SngbaApmqTnQ==\n service-type telnet http ssh terminal\n authorization-attribute user-role network-admin\n authorization-attribute user-role network-operator\n#\n ip http enable\n ip https enable\n#\nreturn\n',
  newString: '#\n version 7.1.070, Release 6343P08\n#\n sysname JR-4300-CR5-S5130-01\n#\n clock timezone Beijing add 08:00:00\n#\n irf mac-address persistent timer\n irf auto-update enable\n undo irf link-delay\n irf member 1 priority 1\n#\n dot1x\n dot1x authentication-method eap\n#\n mac-address notification mac-move\n#\n lldp compliance cdp\n lldp global enable\n#\n password-recovery enable\n#\nvlan 1\n#\nvlan 12\n#\n stp mode pvst\n stp bpdu-protection\n stp pathcost-standard dot1t\n stp global enable\n#\ninterface Bridge-Aggregation1\n port link-type trunk\n port trunk permit vlan all\n link-aggregation mode dynamic\n#\ninterface NULL0\n#\ninterface Vlan-interface1\n ip address 10.89.10.73 255.255.255.0\n dhcp client identifier ascii 7449d299f6d2-VLAN0001\n#\ninterface GigabitEthernet1/0/1\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/2\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/3\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/4\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/5\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/6\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/7\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/8\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/9\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/10\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/11\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/12\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/13\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/14\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/15\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/16\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/17\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/18\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/19\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/20\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/21\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/22\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/23\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/24\n port access vlan 12\n broadcast-suppression 5\n multicast-suppression 5\n stp edged-port\n dot1x\n#\ninterface GigabitEthernet1/0/25\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n port link-aggregation group 1\n#\ninterface GigabitEthernet1/0/26\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n port link-aggregation group 1\n#\ninterface GigabitEthernet1/0/27\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n#\ninterface GigabitEthernet1/0/28\n port link-type trunk\n port trunk permit vlan all\n lldp compliance admin-status cdp txrx\n#\n scheduler logfile size 16\n#\nline class aux\n user-role network-admin\n#\nline class vty\n user-role network-operator\n#\nline aux 0\n user-role network-admin\n#\nline vty 0 4\n authentication-mode scheme\n user-role network-operator\n#\nline vty 5 63\n user-role network-operator\n#\n ip route-static 0.0.0.0 0 10.89.10.1\n#\n info-center loghost source Vlan-interface1\n info-center loghost 10.88.245.31\n info-center loghost 10.99.160.43\n info-center loghost 10.99.216.202\n info-center loghost 10.188.19.194\n#\n snmp-agent\n snmp-agent local-engineid 800063A280AC7409FAEABD00000001\n snmp-agent community write cisco123\n snmp-agent sys-info version all \n snmp-agent target-host trap address udp-domain 10.188.19.194 params securityname cisco123 v2c\n#\n ifmonitor crc-error slot 1 high-threshold 1000 low-threshold 100 interval 30\n ifmonitor input-error slot 1 high-threshold 1000 low-threshold 100 interval 30\n ifmonitor output-error slot 1 high-threshold 1000 low-threshold 100 interval 30\n#\n ssh server enable\n#\n ntp-service enable\n ntp-service unicast-server 10.188.16.101\n#\nradius scheme aaa\n primary authentication 10.88.250.11 key cipher $c$3$trlI9U9Fz1xwETmbsWVLtVDTwtY9cKzO9w==\n secondary authentication 10.88.250.12 key cipher $c$3$H3nJVbdzZesByOleYToP8/JptJ2815pWng==\n#\nradius scheme system\n user-name-format without-domain\n#\ndomain system\n authentication login local\n authorization login local\n authentication default radius-scheme aaa\n authorization default radius-scheme aaa\n#\n domain default enable system\n#\nrole name level-0\n description Predefined level-0 role\n#\nrole name level-1\n description Predefined level-1 role\n#\nrole name level-2\n description Predefined level-2 role\n#\nrole name level-3\n description Predefined level-3 role\n#\nrole name level-4\n description Predefined level-4 role\n#\nrole name level-5\n description Predefined level-5 role\n#\nrole name level-6\n description Predefined level-6 role\n#\nrole name level-7\n description Predefined level-7 role\n#\nrole name level-8\n description Predefined level-8 role\n#\nrole name level-9\n description Predefined level-9 role\n#\nrole name level-10\n description Predefined level-10 role\n#\nrole name level-11\n description Predefined level-11 role\n#\nrole name level-12\n description Predefined level-12 role\n#\nrole name level-13\n description Predefined level-13 role\n#\nrole name level-14\n description Predefined level-14 role\n#\nuser-group system\n#\nlocal-user admin class manage\n password hash $h$6$GNr8ydnrBrwWviX4$ZXJRlHwb6nfjhkYHR+95BeaTb8NjYoF7xa+M2o+dIOqaPdgNMOtama1wfyI1aOV4XAjPWVgbNBPxytdDiCVUEQ==\n service-type telnet ssh\n authorization-attribute user-role network-admin\n authorization-attribute user-role network-operator\n#\nreturn\n',
  language: 'plaintext',
  diffStyle: 'word',
  ignoreMatchingLines: 'version',
})

const changeStatistic = ref({
  equalCont: 0,
  onlyCont: 0,
  changeCont: 0,
  ignoreCont: 0
})

const diffChange = ref<Array<number>>([])

function diffed(e: any) {
  diffChange.value = e.diffChange
  changeStatistic.value = e.stat
  curChange.value = -1
  console.log('diffed', e)
}

const diffViewer = ref<Element | null>(null)

const curChange = ref<number>(-1)

function prevChange() {
  if (curChange.value > 0) {
    curChange.value--
    diffViewer.value.jumpToChange(diffChange.value[curChange.value])
  }
}

function nextChange() {
  if (curChange.value < diffChange.value.length - 1) {
    curChange.value++
    diffViewer.value.jumpToChange(diffChange.value[curChange.value])
  }
}

const contextNum = ref<number>(1000)

function changeDisplay() {
  if (contextNum.value) {
    contextNum.value = 0
  } else {
    contextNum.value = 1000
  }
}

</script>

<template>
  <div>
    <!-- <p align="center">
      Vue version: {{ version }}
    </p> -->
    <textarea v-model="form.oldString" style="width: 40vw" :rows="20" />
    <textarea v-model="form.newString" style="width: 40vw; margin-left: 20px" :rows="20" />
    <CodeDiff
      ref="diffViewer"
      :old-string="form.oldString"
      :new-string="form.newString"
      :language="form.language"
      :diff-style="form.diffStyle"
      :ignore-matching-lines="form.ignoreMatchingLines"
      :hide-header="true"
      :context="contextNum"
      theme="light"
      max-height="350px"
      output-format="side-by-side"
      @diff="diffed"
    />
    <div class="statistic">
      <p>相同的行：{{ changeStatistic.equalCont }}</p>
      <p>变化的行：{{ changeStatistic.changeCont }}</p>
      <p>唯一的行：{{ changeStatistic.onlyCont }}</p>
      <!-- <p>忽略的行：{{ changeStatistic.ignoreCont }}</p> -->
    </div>
    <div class="btn">
      <button :disabled="contextNum && curChange <= 0" @click="prevChange">PREV</button>
      <button :disabled="contextNum && curChange >= diffChange.length - 1" @click="nextChange">NEXT</button>
    </div>
    <div class="btn">
      <button :disabled="!(changeStatistic.changeCont || changeStatistic.onlyCont)" @click="changeDisplay">CHANGE</button>
    </div>
  </div>
</template>

<style>
body > div {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.statistic {
  font-size: 14px;
  display: flex;
  text-align: left;
}
.statistic > p {
  margin-right: 20px;
}
.btn {
  display: flex;
  margin-bottom: 10px;
}
.btn > button {
  margin-right: 20px;
}
</style>
