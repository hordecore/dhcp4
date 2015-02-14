import "dhcp-logging"
import "dhcp-matches"

option ms-classless-static-routes(249) = option rfc3442-classless-static-routes(121) =int[8]
default-lease-time = max-lease-time = 172800
authoritative = true
log-facility = local7

if exists agent.circuit-id:
	dhcp_log_raw()
	dhcp_log_dlink()
	dhcp_log_alter()
	dhcp_log_snr()
	dhcp_log_eltex_lte()

shared-network ISC:
	option domain-name-servers 8.8.8.8
	subnet 192.168.0.253/32:
	subnet 192.168.0.128/26:
	subnet 192.168.0.000/25:
		option routers 192.168.0.1

	### db bindings
	dhcp_match_eltex_switch_ip(192.168.0.1):
		dhcp_match_eltex_vlan(102) and dhcp_match_eltex_port(2):
			range 192.168.0.35
		dhcp_match_eltex_vlan(103) and dhcp_match_eltex_port(3):
			range 192.168.0.36

	dhcp_match_dlink_switch_ip(192.168.0.129):
		dhcp_match_dlink_vlan(104) and dhcp_match_dlink_port(4):
			range 192.168.0.37
		dhcp_match_dlink_vlan(104) and dhcp_match_dlink_port(5):
			range 192.168.0.38
