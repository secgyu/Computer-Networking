# 네트워크 소개
<table>
  <tr>
    <td>
      <ul>
        <li><b>IP 주소:</b> 192.168.45.138</li>
        <li><b>서브넷 마스크:</b> 255.255.255.0</li>
        <li><b>게이트웨이:</b> 192.168.45.1</li>
        <li><b>DHCP 서버:</b> 192.168.45.1</li>
        <li><b>DNS 서버:</b> 8.8.8.8</li>
        <li>— 구글 public DNS 서비스 IP 주소</li>
      </ul>
    </td>
    <td style="text-align: right;">
      <img src="https://github.com/secgyu/Computer-Networking/blob/main/%EC%9D%B4%EB%AF%B8%EC%A7%801.png" alt="네트워크 설정 정보">
    </td>
  </tr>
</table>
<br>
<h2><style="border-bottom: 2px solid black;">도메인 네임, IP 주소, MAC 주소</h2>
<li><b>도메인 네임 : </b> www.example.com</li>
<li><b>IP 주소 : </b> 203.0.113.78</li>
<li><b>MAC 주소 : </b> 02-AB-CD-EF-01-23</li>
<li><b>DNS 서버 : </b> 도메인 네임 → IP 주소</li>
<li><b>ARP 프로토콜 : </b> IP 주소 → MAC 주소</li>
<br>
<h2><style="border-bottom: 2px solid black;">통신방식</h2>
<li><b>유니캐스트(unicast) : </b> 단일 목적지로의 데이터전송</li>
<li><b>브로드캐스트(broadcast):</b> 수신 가능한 모든 목적지로의 데이터 전송</li>
  <ul>
    <li><b>IPv4 broadcast address</b> → 255.255.255.255</li>
    <li><b>MAC broadcast address</b> → FF-FF-FF-FF-FF-FF</li>
  </ul>
<li><b>멀티캐스트(multicast) : </b> 다수 목적지로의 데이터 전송</li>
<li><b>애니캐스트(anycast):</b> 다수 목적지 중 (가장 가까운)하나의 목적지로의 데이터 전송</li>
  <ul>
    <li><b>DNS 루트 네임 서버</b>
  </ul>
<br>
<h2><style="border-bottom: 2px solid black;">호스트, 스위치, 라우터, 통신링크</h2>
<td style="text-align: center;">
      <img src="https://github.com/secgyu/Computer-Networking/blob/main/%EC%9D%B4%EB%AF%B8%EC%A7%802.png" alt="네트워크 설정 정보">
<li><b>호스트(host) : </b>컴퓨터 네트워크에 연결되어 응용프로그램을 실행하는 장치로 end system이라고도 부름</li>
<li><b>스위치(switch) : </b>네트워크 장치들을 연결하며, 연결된 발신 장치로부터 수신된 데이터들을, MAC 주소에 기반하여, 연결된 목적지 장치(들)로 전달하는 장치</li>
<li><b>라우터(router) : </b>컴퓨터 네트워크들을 연결하며, 연결된 한 네트워크로부터 수신된 데이터를, IP 주소에 기반하여, 연결된 다른 네트워크로 전달하는 장치</li>
<li><b>통신링크(전송매체) : </b>꼬임쌍선(twisted pair cable), 광섬유케이블(optical fiber cable)</li>
<br>
<h2><style="border-bottom: 2px solid black;">프로토콜</h2>
<li><b>프로토콜(Protocol) : </b>둘 이상 통신 개체 간 메시지 송수신 규칙 정의</li>
  <ul>
    <li><b>HTTP, DNS, DHCP, RIP, BGP</b></li>
    <li><b>TCP, UDP</b></li>
    <li><b>ICMP, OSPF</b></li>
    <li><b>IP, ARP</b></li>
  </ul>
<br>
<h2><style="border-bottom: 2px solid black;">PDU</h2>
<li><b>PDU(Protocol Data Unit) : </b>컴퓨터 네트워크에서 동일 계층 프로토콜 간 전송되는 정보 단위</li>
  <ul>
    <li><b>TCP → TCP 세그먼트(TCP segment), 세그먼트(segment)</b></li>
    <li><b>UDP → 유저 데이터그램(user datagram)</b></li>
    <li><b>IP → 패킷(packet), IP 데이터그램(IP datagram), 데이터그램(datagram)</b></li>
    <li><b>이더넷(Ethernet) → 프레임(frame), 이더넷 프레임</b></li>
  </ul>
<br>
<h2><style="border-bottom: 2px solid black;">RFC, IETF, IEEE802</h2>
<li><b>RFC(Request For Comments) : </b>IETF에 의해 출판되는 인터넷 기술 관련 문서</li>
<li><b>IETF(Internet Engineering Task Force) : </b>인터넷 표준 개발 기구</li>
<li><b>IEEE 802 LAN/MAN 표준위원회 : </b>IEEE → Institute of Electrical and Electronics Engineers(전기전자기술자협회)</li>
<br>
<h2><style="border-bottom: 2px solid black;">Octet</h2>
<li><b>옥텟(Octet) : </b>8비트로 이루어진 정보 단위를 지칭하는 용어</li>
