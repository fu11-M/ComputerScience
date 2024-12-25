### DNS
DNS(Domain Name System)는 인터넷에서 도메인 이름(예: www.google.com)을 IP 주소(예: 142.250.190.78)로 변환해주는 시스템이다.

인터넷은 IP 주소를 기반으로 통신하지만, 사람이 숫자로 이루어진 IP 주소를 기억하기 어렵기 때문에 도메인 이름을 사용한다.

DNS는 이 도메인 이름을 컴퓨터가 이해할 수 있는 IP 주소로 변환해주는 역할을 한다.

컴퓨터는 모든 데이터를 숫자로 처리하기 때문에 네트워크 통신에서도 IP 주소라는 숫자로 된 주소 체계를 통해 서로를 식별하고 연결한다.


1. DNS의 기본 원리
DNS는 기본적으로 분산된 데이터베이스 시스템입니다. 이를 통해 전 세계에 걸쳐 도메인 이름을 관리하고, 사용자 요청에 대해 빠르게 IP 주소를 반환할 수 있습니다. DNS는 다음과 같은 과정으로 작동합니다:

사용자 요청: 웹 브라우저에서 도메인 이름을 입력하면, 해당 도메인에 대한 IP 주소를 찾기 위한 요청이 DNS 서버에 전송됩니다.
DNS 쿼리: DNS 서버는 여러 단계의 쿼리를 통해 IP 주소를 찾습니다. 처음에는 로컬 DNS 캐시에서 정보를 찾고, 없다면 다른 DNS 서버로 요청을 전달합니다.
IP 주소 반환: 최종적으로 IP 주소가 발견되면, 브라우저는 이 주소를 통해 웹사이트에 접속할 수 있습니다.
2. DNS의 계층 구조
DNS는 계층적인 구조를 가지고 있습니다. 이 구조는 크게 루트 DNS 서버, 최상위 도메인(TLD) DNS 서버, 권한 있는 DNS 서버로 나눌 수 있습니다.

루트 DNS 서버: DNS 시스템의 최상위에 존재하며, 전 세계에 13개의 루트 DNS 서버가 분포해 있습니다. 루트 서버는 TLD 서버의 위치 정보를 알고 있으며, 도메인 이름이 .com, .org, .net과 같은 최상위 도메인에 속하는지 확인합니다.

TLD DNS 서버: 최상위 도메인(TLD)은 예를 들어 .com, .org, .kr과 같은 부분입니다. TLD 서버는 해당 도메인의 레코드를 찾을 수 있는 정보를 가지고 있으며, 이를 바탕으로 권한 있는 DNS 서버로 요청을 전달합니다.

권한 있는 DNS 서버: 권한 있는 DNS 서버는 실제 도메인에 대한 정보를 관리합니다. 예를 들어, example.com 도메인에 대한 정보는 example.com의 DNS 서버에 저장됩니다.

3. DNS 레코드 유형
DNS는 여러 가지 유형의 레코드를 사용하여 도메인과 관련된 다양한 정보를 저장합니다. 주요 레코드 유형은 다음과 같습니다:

A 레코드 (Address Record): 도메인 이름을 IPv4 주소에 매핑합니다. 예: www.example.com -> 192.168.1.1

AAAA 레코드: 도메인 이름을 IPv6 주소에 매핑합니다. 예: www.example.com -> 2001:0db8:85a3:0000:0000:8a2e:0370:7334

CNAME 레코드 (Canonical Name Record): 하나의 도메인 이름을 다른 도메인 이름에 매핑합니다. 예: www.example.com -> example.com

MX 레코드 (Mail Exchange Record): 이메일 서버의 정보를 제공하며, 특정 도메인의 이메일을 처리하는 서버를 지정합니다. 예: example.com -> mail.example.com

NS 레코드 (Name Server Record): 해당 도메인의 권한 있는 DNS 서버를 지정합니다. 예: example.com -> ns1.example.com

TXT 레코드: 도메인에 대한 텍스트 정보를 저장합니다. 주로 이메일 인증을 위한 SPF, DKIM과 같은 데이터를 포함합니다.

PTR 레코드 (Pointer Record): IP 주소를 도메인 이름으로 역으로 변환하는 데 사용됩니다. 주로 리버스 DNS 조회에 사용됩니다.

4. DNS 캐싱
DNS는 성능 향상과 네트워크 트래픽 절감을 위해 캐시 메커니즘을 사용합니다. DNS 레코드는 일정 기간 동안 캐시되어, 동일한 도메인에 대한 후속 요청은 더 빠르게 처리할 수 있습니다. DNS 레코드에는 TTL(Time to Live) 값이 지정되어 있으며, TTL이 만료되면 해당 레코드는 캐시에서 제거되고 새로운 쿼리가 발생합니다.

5. DNS의 보안
DNS는 본래 보안에 취약한 설계였으므로, 이를 보호하기 위한 여러 기술들이 개발되었습니다.

DNSSEC (DNS Security Extensions): DNS의 무결성을 보장하고, 악의적인 변조나 공격을 방지하기 위해 DNS에 전자 서명을 추가하는 기술입니다.
DoH (DNS over HTTPS): DNS 쿼리와 응답을 HTTPS 프로토콜로 암호화하여 프라이버시를 강화하는 방식입니다.
DoT (DNS over TLS): DNS 쿼리와 응답을 TLS 암호화로 보호하여 보안을 강화합니다.
6. DNS 공격
DNS는 여러 가지 공격에 노출될 수 있습니다. 대표적인 공격 방법은 다음과 같습니다:

DNS 스푸핑 (DNS Spoofing): 악의적인 사용자가 DNS 응답을 변조하여 사용자를 잘못된 웹사이트로 유도하는 공격입니다.
DDoS 공격 (Distributed Denial of Service): 대규모의 트래픽을 DNS 서버에 보내서 서버를 마비시키는 공격입니다.
DNS 하이재킹: 공격자가 DNS 서버 설정을 변경하여 사용자를 악의적인 사이트로 리다이렉션하는 공격입니다.