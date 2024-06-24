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
