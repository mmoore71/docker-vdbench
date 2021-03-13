# Oracle JRE 8
FROM nimmis/java-centos:oracle-8-jre

# copy vdbench
COPY vdbench /vdbench

# runs vdbench in interactive mode
ENTRYPOINT [ "/vdbench/vdbench", "rsh" ]