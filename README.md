# north-dakota
rom announce-return-187-apmail-httpd-announce-archive=httpd.apache.org@httpd.apache.org  Mon Mar 26 15:36:52 2018
Return-Path: <announce-return-187-apmail-httpd-announce-archive=httpd.apache.org@httpd.apache.org>
X-Original-To: apmail-httpd-announce-archive@www.apache.org
Delivered-To: apmail-httpd-announce-archive@www.apache.org
Received: from mail.apache.org (hermes.apache.org [140.211.11.3])
	by minotaur.apache.org (Postfix) with SMTP id 44AF0186E8
	for <apmail-httpd-announce-archive@www.apache.org>; Mon, 26 Mar 2018 15:36:52 +0000 (UTC)
Received: (qmail 50912 invoked by uid 500); 26 Mar 2018 15:33:01 -0000
Delivered-To: apmail-httpd-announce-archive@httpd.apache.org
Received: (qmail 50815 invoked by uid 500); 26 Mar 2018 15:33:01 -0000
Mailing-List: contact announce-help@httpd.apache.org; run by ezmlm
Precedence: bulk
list-help: <mailto:announce-help@httpd.apache.org>
list-unsubscribe: <mailto:announce-unsubscribe@httpd.apache.org>
List-Post: <mailto:announce@httpd.apache.org>
List-Id: <announce.httpd.apache.org>
Delivered-To: mailing list announce@httpd.apache.org
Delivered-To: moderator for announce@httpd.apache.org
Received: (qmail 24569 invoked by uid 99); 26 Mar 2018 05:06:22 -0000
X-Virus-Scanned: Debian amavisd-new at spamd4-us-west.apache.org
X-Spam-Flag: NO
X-Spam-Score: 2.626
X-Spam-Level: **
X-Spam-Status: No, score=2.626 tagged_above=-999 required=6.31
	tests=[RCVD_IN_SORBS_DUL=0.001, RDNS_DYNAMIC=0.363,
	SPF_SOFTFAIL=0.972, TO_NO_BRKTS_DYNIP=1.29] autolearn=disabled
To: announce@httpd.apache.org, oss-security@lists.openwall.com,
    security@httpd.apache.org
Subject: CVE-2018-1283: Tampering of mod_session data for CGI applications
From: Daniel Ruggeri <druggeri@apache.org>
Reply-To: security@httpd.apache.org
Message-Id: <E1f0KKp-000374-B8@romulus.home.bitnebula.com>
Date: Mon, 26 Mar 2018 00:06:19 -0500


CVE-2018-1283: Tampering of mod_session data for CGI applications.

Severity: Medium

Vendor: The Apache Software Foundation

Versions Affected:
httpd 2.4.0 to 2.4.29

Description:

When mod_session is configured to forward its session data to CGI
applications (SessionEnv on, not the default), a remote user may influence
their content by using a "Session" header. This comes from the "HTTP_SESSION"
variable name used by mod_session to forward its data to CGIs, since the
prefix "HTTP_" is also used by the Apache HTTP Server to pass HTTP header
fields, per CGI specifications.

The severity is set to Medium because "SessionEnv on" is not a default nor
common configuration, it should be considered High when this is the case
though, because of the possible remote exploitation.

Mitigation:
All httpd users should upgrade to 2.4.30 or later.

Credit:
The issue was discovered internally by the Apache HTTP Server team.

References:
https://httpd.apache.org/security/vulnerabilities_24.html
