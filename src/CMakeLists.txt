
add_library(netfilter_conntrack SHARED
	conntrack/api.c
	conntrack/getter.c
	conntrack/setter.c
	conntrack/labels.c
	conntrack/parse.c
	conntrack/build.c
	conntrack/parse_mnl.c
	conntrack/build_mnl.c
	conntrack/snprintf.c
	conntrack/snprintf_default.c
	conntrack/snprintf_xml.c
	conntrack/objopt.c
	conntrack/compare.c
	conntrack/copy.c
	conntrack/filter.c
	conntrack/bsf.c
	conntrack/filter_dump.c
	conntrack/grp.c
	conntrack/grp_getter.c
	conntrack/grp_setter.c
	conntrack/stack.c
	expect/api.c
	expect/compare.c
	expect/getter.c
	expect/setter.c
	expect/parse.c
	expect/build.c
	expect/snprintf.c
	expect/snprintf_default.c
	expect/snprintf_xml.c
	expect/build_mnl.c
	expect/parse_mnl.c
	main.c
	callback.c
)

install(TARGETS netfilter_conntrack DESTINATION lib)
