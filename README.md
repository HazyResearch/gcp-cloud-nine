# Cloud Nine
Cloud tools for managing infrastructure on AWS and Google Cloud.

### Random Commands

To create an instance with A100 16 GPUs Preemtible in central-1b.

```
gcloud compute instances create preem-16a100 \
   --project hai-gcp-disambiguation \
   --zone us-central1-b \
   --machine-type a2-megagpu-16g \
   --maintenance-policy TERMINATE --restart-on-failure \
   --image-family pytorch-1-7-cu110-ubuntu-1804 \
   --image-project deeplearning-platform-release \
   --accelerator='type=nvidia-tesla-a100,count=16' \
   --boot-disk-size 200GB \
   --metadata "install-nvidia-driver=True,proxy-mode=project_editors" \
   --preemptible

```

You can then ssh onto the machine via

`gcloud beta compute ssh --zone "us-central1-b" "preem-16a100"  --project "<PROJECT_NAME>"`

If you install stuff and want to save the image, you can do so in the VM Instance page. Select the save image option in the dotted extra options to the side.