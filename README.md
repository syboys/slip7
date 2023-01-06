# slip7


Q.1 Write a Java Program to implement undo command to test Ceiling fan. 
Q.2. Write a python program to implement Naive Bayes. 
Q. 3 Create a Node.js file that writes an HTML form, with an upload field.




Q.1 Write a Java Program to implement undo command to test Ceiling fan.

:
interface Command {
 public void execute();
}
class CeilingFan {
 public void on(){
 System.out.println("Ceiling Fan is on");
 }
 public void off()
 {
 System.out.println("Ceiling Fan is off");
 }
}
 class CeilingFanOnCommand implements Command {
 CeilingFan c;

 public CeilingFanOnCommand(CeilingFan l) {
 this.c = l;
 }

 public void execute() {
 c.on();
 } 
}
 class CeilingFanOffCommand implements Command {
CeilingFan c;
public CeilingFanOffCommand(CeilingFan l) {
this.c = l;
}
public void execute() {
c.off();
}
}
 class SimpleRemoteControl {
 Command slot;

 public SimpleRemoteControl() {}

 public void setCommand(Command command) {
 slot = command;
 }

 public void buttonWasPressed() {
 slot.execute();
 }

}
public class Main {
 public static void main(String[] args) {
 SimpleRemoteControl remote = new SimpleRemoteControl();
 CeilingFan ceilingFan=new CeilingFan();
 CeilingFanOnCommand ceilingFanOn =new CeilingFanOnCommand(ceilingFan);
 remote.setCommand(ceilingFanOn);
 remote.buttonWasPressed();

CeilingFanOffCommand ceilingFanOff =new CeilingFanOffCommand(ceilingFan);
 remote.setCommand(ceilingFanOff);
 remote.buttonWasPressed();


 }
}


Q.2. Write a python program to implement Naive Bayes.
:

from collections import Counter

def fit(X, y):
    """Fit a Naive Bayes model to the training data.

    Parameters
    ----------
    X : array-like, shape (n_samples, n_features)
        The training input samples.
    y : array-like, shape (n_samples,)
        The target values.

    Returns
    -------
    self : object
        Returns self.
    """
    # Count the number of samples in each class
    self.class_counts = Counter(y)

    # Count the number of occurrences of each feature value for each class
    self.feature_counts = {}
    for label in self.class_counts.keys():
        self.feature_counts[label] = {}
        for i in range(self.n_features):
            self.feature_counts[label][i] = Counter(X[y == label, i])

    # Compute the prior probabilities for each class
    self.priors = {label: count / self.n_samples
                   for label, count in self.class_counts.items()}

    return self

def predict_proba(self, X):
    """Predict class probabilities for the input samples.

    Parameters
    ----------
    X : array-like, shape (n_samples, n_features)
        The input samples.

    Returns
    -------
    proba : array, shape (n_samples, n_classes)
        The class probabilities for the input samples.
    """
    proba = []
    for sample in X:
        # Compute the probability for each class
        class_proba = {}
        for label, prior in self.priors.items():
            # Compute the likelihood of each feature value given the class
            likelihood = 1
            for i, value in enumerate(sample):
                likelihood *= self.feature_proba(i, value, label)

            # Compute the posterior probability for the class
            class_proba[label] = prior * likelihood

        # Normalize the probabilities
        normalization = sum(class_proba.values())
        for label in class_proba:
            class_proba[label] /= normalization

        proba.append(class_proba)
    return proba

def predict(self, X):
    """Predict the class labels for the input samples.

    Parameters
    ----------
    X : array-like, shape (n_samples, n_features)
        The input samples.

    Returns
    -------
    y : array, shape (n_samples,)
        The predicted class labels.
    """
    proba = self.predict_proba(X)
    return [max(p, key=p.get) for p in proba]

def feature_proba(self, feature_index, value, label):
    """Compute the probability of a feature value given a class.

    Parameters
    ----------
    feature_index : int
        The index of the feature.
    value : any
        The value of the feature.
    label : any
        The class label.

    Returns
    -------
    prob


Q. 3 Create a Node.js file that writes an HTML form, with an upload field.
:
var http = require('http');
var formidable = require('formidable'); //module is used for
parsing form data, for handling incoming form data and file
uploads
http.createServer(function(req,res){
 var form = new formidable.IncomingForm(); //Creates a new
incoming form.
 form.parse(req,function(err,fields,files){
 if(req.url=='/fileupload'){ //if user request of
uploading file is successful then "File Uploaded Successfully"
 console.log(files);
 res.write('File Uploaded');
 res.end();
 }
 else{
 res.writeHead(200,{'Content-Type':'text/html'});
 //enctype multipart is used for dealing with files,
usually 'text' is the type for pass,name,email
 res.write('<form action = "fileupload" method =
"get" enctype = "multipart/form_data">');
 res.write('<input type = "file"
name="fileuploaded"><br><br>');
 res.write('<input type = "submit">');
 res.write('</form>');
 return res.end();
 }
 });
}).listen(8080);

