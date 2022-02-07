### Commands

`terraform init` 

Initialize infrastructure from the main.tf file

`terraform plan` 

Displays the changes that will be made to the environment once applied

`terraform apply` 

Applies the changes 

`terraform refresh` 

If there were manual changes, or any changes made by drift...refresh sets environment to original state

`terraform destroy` 

Destroys infrastructure built by apply


# save plan output to file
terraform plan | tee -a outfile

# remove ANSI escape and color characters
cat outfile | gsed -r "s/[[:cntrl:]]\[[0-9]{1,3}m//g" > outfileclean

# grep for additions/modifications/removals
cat outfileclean | grep -e "^  +" -e "^  ~" -e "^  -"

# generate param string to tack to 'terraform apply' with pre-populated targets
# note: modify grep expressions according to your need
cat outfileclean | grep -e "^  +" -e "^  ~" -e "^  -" | grep launch_template | awk '{print $2}' | sed 's/^/-target /' | xargs

