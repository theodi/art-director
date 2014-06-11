art-director
============

Rackspace's DNS will (quite sensibly) not allow us to have a CNAME for a domain's apex. So instead, we make two A records _per_ https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages#apex-domains:

    weneedus.org A 192.30.252.153
    weneedus.org A 192.30.252.154

with _www_ CNAMEd to the Heroku app as you'd expect:

    www.weneedus.org CNAME powerful-retreat-1036.herokuapp.com

Then all we have in this repo (on the _gh-pages_ branch) is an immediate meta-refresh (which apparently your browser will treat as a proper 302):

    <meta http-equiv="refresh" content="0; url=http://www.weneedus.org/">

and the hack is complete
