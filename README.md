# this file will help to fetch the revision bamboo build plan for perticuler build-number
# both build-plan name and build-number need to be provided while running the script

# Bamboo CLI plugin is installed in bamboo while running the script
# Bamboo Command lines connector should be available in the system

./bamboo.sh --action getBuild --file "getBuildWithResultName.txt" --build "UMESH-UCP-2"
var=$(cat getBuildWithResultName.txt | grep vcsRevisionKey)
echo $var
revision=$(echo $var |cut -d' ' -f9)
echo $revision
./bamboo.sh --action queueBuild --plan "UMESH-UCP" --revision $revision
