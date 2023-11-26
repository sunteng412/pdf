fork from  https://github.com/rsc/pdf

support chinese character

update log 
date: 2023-11-26 17:12:00
1. add close file method
2. add chinese character support


example
```go
func TestChinesePDFAnalyze(t *testing.T) {
    file, err := pdf.Open("/Users/Downloads/chinesePdf.pdf")
    if err != nil {
        log.Println("error open file", err)
    }

    //close pdf file and clean localCache
    defer pdf.Close()

    str := ""
    for i := 0; i < file.NumPage(); i++ {
        content := file.Page(i + 1).Content()
        for _, text := range content.Text {
        str += text.S
        }
    }

    fmt.Println(str)
}
```

