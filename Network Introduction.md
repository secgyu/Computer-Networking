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

## 도메인 네임, IP 주소, MAC 주소
- **도메인 네임:** www.example.com
- **IP 주소:** 203.0.113.78
- **MAC 주소:** 02-AB-CD-EF-01-23
- **DNS 서버:** 도메인 네임 → IP 주소
- **ARP 프로토콜:** IP 주소 → MAC 주소

## 통신방식
- **유니캐스트(unicast):** 단일 목적지로의 데이터전송
- **브로드캐스트(broadcast):** 수신 가능한 모든 목적지로의 데이터 전송
  - **IPv4 broadcast address** → 255.255.255.255
  - **MAC broadcast address** → FF-FF-FF-FF-FF-FF
- **멀티캐스트(multicast):** 다수 목적지로의 데이터 전송
- **애니캐스트(anycast):** 다수 목적지 중 하나의 목적지로의 데이터 전송
  - **DNS 루트 네임 서버**

## 호스트, 스위치, 라우터, 통신링크
![네트워크 설정 정보](https://github.com/secgyu/Computer-Networking/blob/main/%EC%9D%B4%EB%AF%B8%EC%A7%802.png)
- **호스트(host):** 컴퓨터 네트워크에 연결되어 응용프로그램을 실행하는 장치, end system이라고도 부름
- **스위치(switch):** 네트워크 장치들을 연결하며, 연결된 발신 장치로부터 수신된 데이터들을, MAC 주소에 기반하여, 연결된 목적지 장치(들)로 전달하는 장치
- **라우터(router):** 컴퓨터 네트워크들을 연결하며, 연결된 한 네트워크로부터 수신된 데이터를, IP 주소에 기반하여, 연결된 다른 네트워크로 전달하는 장치
- **통신링크(전송매체):** 꼬임쌍선(twisted pair cable), 광섬유케이블(optical fiber cable)

## 프로토콜
- **프로토콜(Protocol):** 둘 이상 통신 개체 간 메시지 송수신 규칙 정의
  - **HTTP, DNS, DHCP, RIP, BGP**
  - **TCP, UDP**
  - **ICMP, OSPF**
  - **IP, ARP**

## PDU
- **PDU(Protocol Data Unit):** 컴퓨터 네트워크에서 동일 계층 프로토콜 간 전송되는 정보 단위
  - **TCP → TCP 세그먼트(TCP segment), 세그먼트(segment)**
  - **UDP → 유저 데이터그램(user datagram)**
  - **IP → 패킷(packet), IP 데이터그램(IP datagram), 데이터그램(datagram)**
  - **이더넷(Ethernet) → 프레임(frame), 이더넷 프레임**

## RFC, IETF, IEEE802
- **RFC(Request For Comments):** IETF에 의해 출판되는 인터넷 기술 관련 문서
- **IETF(Internet Engineering Task Force):** 인터넷 표준 개발 기구
- **IEEE 802 LAN/MAN 표준위원회:** IEEE → Institute of Electrical and Electronics Engineers(전기전자기술자협회)

## Octet
- **옥텟(Octet):** 8비트로 이루어진 정보 단위를 지칭하는 용어
