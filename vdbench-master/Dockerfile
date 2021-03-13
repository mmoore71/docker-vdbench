# Oracle JRE 8
FROM nimmis/java-centos:oracle-8-jre

# copy vdbench
COPY vdbench /vdbench

# Set environment variables.
ENV HOME /vdbench

# Define working directory.
WORKDIR /vdbench

# Define default command.
ENTRYPOINT [ "bash" ]