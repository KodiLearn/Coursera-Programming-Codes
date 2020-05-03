import edu.duke.*;
import java.util.Scanner;
/**
 * This findGene java class is used to find multiple genes from the file or text.
 * 
 * @author (Binamra Lamsal) 
 * @version (1.0)
 */
public class findGene {
    
    // To find the cgRatio of each gene
    public double cgRatio(String gene){ 
        int currIndex = 0;
        int cgSum = 0;
        int cLocation = gene.indexOf("C"); // To find the location of C in gene
        
        while (cLocation != -1){
            cgSum += 1; 
            cLocation = gene.indexOf("C", cLocation + 1); // To find the location of C after the previous location
        }
        
        int gLocation = gene.indexOf("G"); // To find the location of G in gene
        while (gLocation != -1){
            cgSum += 1;
            gLocation = gene.indexOf("G", gLocation + 1); // To find the location of G after the previous location
        }
        
        return (double) cgSum / gene.length(); // Returns the cgRatio
    }
    
    // To print all Genes in dna and other information
    public void printAllGenes(String dna){
        int startIndex = 0;
        int geneCount = 0;
        int cgRatioCount = 0;
        int greaterThen60 = 0;
        int ctgPos = dna.indexOf("CTG", 0);
        int ctgCount = 0;
        
        System.out.println("DNA strand:");
        System.out.println(dna); // To print the DNA
        System.out.println();
        System.out.println("All the Genes are:");
        String longestGene = "";
        
        while (ctgPos != -1){
        ctgPos = dna.indexOf("CTG", ctgPos);
        if (ctgPos == -1){
            break;
        }
        ctgCount += 1;
        ctgPos = ctgPos + 3;
        }
        
        while (true){
            String currentGene = findGene(dna, startIndex); // To find the gene after the startIndex location
            if (currentGene.isEmpty()){
                break;
            }
            geneCount += 1;
            if (currentGene.length() > 60){
                greaterThen60 += 1;
            }
            System.out.println(currentGene); 
            double cgRatio = cgRatio(currentGene); // To find the cgRatio of the gene
            System.out.println("Cg ratio: " + cgRatio);
            if (cgRatio >= 0.35){ // To count the gene whose cgRatio is greater then 0.35
                cgRatioCount += 1;
            }
            if (currentGene.length() > longestGene.length()){ // To find the longest gene
                longestGene = currentGene;
            }
            startIndex = dna.indexOf(currentGene, startIndex) + currentGene.length(); // To get the index after the gene
        }
        
        System.out.println();
        System.out.println("Total Genes found in DNA strand: " + geneCount);
        System.out.println();
        System.out.println("Longest Gene found in DNA strand: ");
        System.out.println(longestGene);
        System.out.println();
        System.out.println("Length of longest gene found in DNA strand is: " + longestGene.length());
        System.out.println();
        System.out.println("CgRatio greater then 0.35 are: " + cgRatioCount);
        System.out.println();
        System.out.println("Genes greater then 60 are: " + greaterThen60);
        System.out.println();
        System.out.println("CTG appears " + ctgCount + " in DNA strand");
    }
    
    // To find the index of stop codon
    public int findStopCodon(String dnaStr, int startIndex, String stopCodon){
        int currIndex = dnaStr.indexOf(stopCodon, startIndex);
        
        while (currIndex != -1){
            if ((currIndex - startIndex) % 3 == 0){
                return currIndex;
            }
            else{
                currIndex = dnaStr.indexOf(stopCodon, currIndex + 1);
            }
        }
        
        return -1;
    }
    
    // To find the first stop codon after the ATG codon
    public String findGene(String dna, int where){
    int startIndex = dna.indexOf("ATG", where);
    
    if (startIndex == -1){
        return "";
    }
    
    // To find the Index of stop codons
    int taaIndex = findStopCodon(dna, startIndex, "TAA"); 
    int tgaIndex = findStopCodon(dna, startIndex, "TGA");
    int tagIndex = findStopCodon(dna, startIndex, "TAG");
    int minIndex = 0;
    
    // To find which stop codon is at the first after start codon
    if (taaIndex == -1 || (tgaIndex != -1 && tgaIndex <taaIndex)){
        minIndex = tgaIndex;
    }
    else{
        minIndex = taaIndex;
    }
    
    if (minIndex == -1 || (tagIndex != -1 && tagIndex < minIndex)){
        minIndex = tagIndex;
    }
    
    if (minIndex == -1){
        return "";
    }
    
    return dna.substring(startIndex, minIndex + 3);
}
    // To count the genes from text
    public void geneFindInText(){
        String dna = "oneAtGMyGeneOneAATGGGGTAATGATAGAACCCGGYGGGGTAGGGCTGCCCATGendOneTAAnonCodingDnaTAGTGAZZZtaaTwoATGMyGeneTwoCATGGGGTAATGATAGCCatgCCCFalseStartTAATGATGendTwoTAGnonCodingDNATAACCCThreeATGMyGeneThreeATGGGGTAATGATAGATGccendThreeTAAnonCodingDNAccTAAfalsecccFourATGMyGeneFourATGGGGTAATGATAGCendFourTAGnonCodingdnaFiveAtgMyGeneFiveATGGGGTAATGATAGCendFiveTGAnonCodingdnaSixATGmyGeneSixATATGGGGTAATGATAGAendSixTAAnoncodingdnaSevenATGMyGeneSevenCcATGGGGTAATGATAGendSeventaAnoncodingdnaEightATGmyGeneEightATGGGGTAATGATAGGGendEighttaAnoncodingdnaCcccWrongtgaCtaaCtagCCcgNineATgmyGeneNineATGGGGTAATGATAGTaaAendNineTAAnonCodingDnaCcccTenATGmyGeneTenGATGGGGTAATGATAGCCHasFakeATGFAKEatgcendTentaanonCodingDnaCtagCtganonCodingDnaxxxElevenATGmyGeneElevenCATGGGGTAATGATAGTAAxxGeneATGTAACATGTAAATGCendElevenTAAnonCodingDnaxTAGxtgaTwelveATGmyGeneTwelveCATGGGGTAATGATAGCTheLastGeneIsATGTAGendTwelvetgaATGTAG";
        printAllGenes(dna.toUpperCase());
    }
    
    // To find the genes from the file
    public void geneFindInFile(){
        FileResource fr = new FileResource();
        String dna = fr.asString();
        printAllGenes(dna.toUpperCase());
    }
    
    // To find the genes from the URL
    public void geneFindInUrl(){
        
        while (true){
            
        try{
            System.out.println();
            System.out.println("Type URL of dna");
            Scanner scanner = new Scanner(System.in);
            String url = scanner.nextLine();
            URLResource ur = new URLResource(url);
            String dna = ur.asString();
            printAllGenes(dna.toUpperCase());
            break;
        }
        
        catch(edu.duke.ResourceException exception){
            System.out.println("Error connecting the server!");
            System.out.println("Try this to fix:");
            System.out.println("i) Check if you are connected to the internet");
            System.out.println("ii) Reconnecting to Wi-Fi");
            System.out.println("ii) Check if you wrote URL with http or https");
            System.out.println("iii) Check the proxy, firewall, and DNS settings.");
            System.out.println("iv) Run Windows Network Diagnostics");
            System.out.println("Error code: [URL_RESOURCE_NOT_FOUND]");
            System.out.println();
            continue;
        }
        
        }
    }
}
