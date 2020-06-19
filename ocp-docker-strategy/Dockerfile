FROM busybox

RUN echo 'while true; do echo "hello current timestamp is : $(date +%Y%m%d-%H:%M:%S)"; sleep 10;done' > /run-cmd.sh
RUN chmod +x /run-cmd.sh
CMD /run-cmd.sh

