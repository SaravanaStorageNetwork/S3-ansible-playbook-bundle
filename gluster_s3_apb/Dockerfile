FROM ansibleplaybookbundle/apb-base

LABEL "com.redhat.apb.spec"=\
"dmVyc2lvbjogMS4wCm5hbWU6IGdsdXN0ZXItczMtYXBiCmRlc2NyaXB0aW9uOiBHbHVzdGVyRlMg\
UzMgb2JqZWN0IHNlcnZpY2UKYmluZGFibGU6IEZhbHNlCmFzeW5jOiBvcHRpb25hbAptZXRhZGF0\
YToKICBkaXNwbGF5TmFtZTogR2x1c3RlckZTIFMzIG9iamVjdCBzZXJ2aWNlCnBsYW5zOgogIC0g\
bmFtZTogZGVmYXVsdAogICAgZGVzY3JpcHRpb246IFRoaXMgcGxhbiBkZXBsb3lzIGdsdXN0ZXIt\
czMtYXBiCiAgICBmcmVlOiBUcnVlCiAgICBtZXRhZGF0YToge30KICAgIHBhcmFtZXRlcnM6IFtd\
CiMgICAgICAtIHRpdGxlOiBPcGVuU2hpZnQgQWRtaW4gVXNlcgojICAgICAgICBuYW1lOiBhZG1p\
bl91c2VyCiMgICAgICAgIHR5cGU6IHN0cmluZwojICAgICAgICByZXF1aXJlZDogdHJ1ZQojICAg\
ICAgLSB0aXRsZTogT3BlblNoaWZ0IEFkbWluIFBhc3N3b3JkCiMgICAgICAgIG5hbWU6IGFkbWlu\
X3Bhc3N3b3JkCiMgICAgICAgIHR5cGU6IHN0cmluZwojICAgICAgICByZXF1aXJlZDogdHJ1ZQoj\
ICAgICAgICBkaXNwbGF5X3R5cGU6IHBhc3N3b3JkCg=="

COPY playbooks /opt/apb/actions
COPY roles /opt/ansible/roles
RUN chmod -R g=u /opt/{ansible,apb}

RUN yum  install sed bash wget which -y #&& yum clean all

#RUN wget https://github.com/openshift/origin/releases/download/v3.9.0/openshift-origin-client-tools-v3.9.0-191fece-linux-64bit.tar.gz
#RUN tar zxvf openshift-origin-client-tools-v3.9.0-191fece-linux-64bit.tar.gz
#RUN mv openshift-origin-client-tools-v3.9.0-191fece-linux-64bit/oc /usr/bin
#RUN rm -rf openshift-origin-client-tools-v3.9.0-191fece-linux-64bit
#RUN chmod u+x /usr/bin/oc

USER apb
