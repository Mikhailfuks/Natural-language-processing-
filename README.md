import edu.stanford.nlp.ling.CoreAnnotations;
import edu.stanford.nlp.ling.CoreLabel;
import edu.stanford.nlp.pipeline.Annotation;
import edu.stanford.nlp.pipeline.StanfordCoreNLP;
import edu.stanford.nlp.util.CoreMap;
// We are making a portal for a website that will help us learn languages
import java.util.List;
import java.util.Properties;
import java.util.ArrayList;
import java.util.Collection ;
import java.util.add;
// We use the libraries we need
public class NaturalLanguageProcessing {

    public static void main(String[] args) {
        // Configuring the Stanford CoreNLP Configuration
        Properties props = new Properties();
        props.setProperty("annotators", "tokenize, ssplit, pos, lemma, ner");
        StanfordCoreNLP pipeline = new StanfordCoreNLP(props);

        // Text for analysis
        String text = ("Я живу в Москве, столице России. Сегодня я иду на работу.");

        // Creating an Annotation object
        Annotation annotation = new Annotation(text);

        // Starting text analysis
        pipeline.annotate(annotation);

        // Getting a list of offers
        List<CoreMap> sentences = annotation.get(CoreAnnotations.SentencesAnnotation.class);

        // Output information about each offer
        for (CoreMap sentence : sentences) {
            System.out.println("Предложение: " + sentence.toString());

            // Getting tokens
            for (CoreLabel token : sentence.get(CoreAnnotations.TokensAnnotation.class)) {
                // Token text output
                System.out.print(token.get(CoreAnnotations.TextAnnotation.class) + " ");

                // Output of a part of speech
                System.out.print("(" + token.get(CoreAnnotations.PartOfSpeechAnnotation.class) + ") ");

                // Output of a named entity
                System.out.print("[" + token.get(CoreAnnotations.NamedEntityTagAnnotation.class) + "] ");

                // The conclusion of the lemma
                System.out.println(token.get(CoreAnnotations.LemmaAnnotation.class));
            }
            System.out.println();
        }
    }
}
// We have created an application that will teach different languages
