# CAPIT-docker

## Usage 

To use:

1. Fill in the .env_template with your own values and rename it to .env
2. Build the image with `docker built -t <container_name> docker/<accelerator-type>/`
3. Run the container with `docker run --name <container-instance-name> --env-file .env -v /mnt/nas/:/mnt/nas/ -it <container_name>`

🐈 Have fun.