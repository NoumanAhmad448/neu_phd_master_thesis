   <h1 align='center'>
      Northeastern University (Shenyang) 东大沈阳 LaTeX Thesis 论文 Template
   </h1>
<h2 align='center'>
   Happy writing thesis ! 祝家人们写毕业论文快乐
</h2>


## Template Structure
```

Thesis/
├── Style/
│ ├── artratex.sty # Main style package
│ ├── neuthesis.cls # Class implementation
│ └── neuthesis.cfg # Configuration labels
├── Tex/
│ ├── FrontPages.tex # Front matter templates
│ └── ... # Other template files
└── Thesis.tex # Main document

````

## Blind Review Configuration

### Option 1: Global Blind Review
1. Edit `Thesis.tex`: include ```blindreview``` to enable blind review otherwise exlude it.
   ```latex
   \usepackage[bibtex,myhdr,table,list,geometry,blindreview]{Style/artratex}

Next find the line
```latex
blindreviewfalse
```
and replace it with
```
blindreviewtrue
```
## How to start writing thesis? 
1. Go to Tex folder and create a folder of your choice. we recommend creating a file name aligned with chapter number. for instance, chapter 1 should be written in chap_1.tex.
2. If you follow the above mentioned rule, you may create another file called ```Chap_2.tex```in a ```Tex``` folder and add that file in ```Tex/Mainmatter.tex``` file by importing it. For import you may use ```input``` command/function.
3. Abstract should be in ```Tex/Abstract.tex``` file.

   
### Custom Blind Review Fields

To create custom blind review fields:

1. Add label in `Style/neuthesis.cfg`:
   ```latex
   \def\neu@label@customfield{Custom Field:}
   ```
2. Implement logic in `Style/neuthesis.cls`:
   ```latex
   \newif\ifcustomblind
   \newcommand{\customblind}[1]{\customblindtrue\def\neu@value@customfield{#1}}
   ```

## Language Switching Mechanism

The template uses a consistent naming pattern:

- English commands: `\neu@label@englishword`
- Chinese commands: `\neu@label@chineseword`

### To find translations:

1. Search for root word in `Style/neuthesis.cfg`:

   ```latex
   % For English institute:
   \def\neu@label@institute{Institute:}

   % Corresponding Chinese version:
   \def\neu@label@chineseinstitute{学院:}
   ```

## Key Features

1. **Dual Language Support**: All labels have English/Chinese versions
2. **Conditional Display**:
   ```latex
   \ifblindreview
     % Hidden content
   \else
     % Visible content
   \fi
   ```
3. **Front Matter Templates**: Predefined title pages, declarations, etc.
4. **Automatic Formatting**: Proper margins, fonts, and spacing for NEU requirements

## Development Notes

1. **Command Implementation**:

   - Defined in `neuthesis.cls`
   - Default values in `neuthesis.cfg`

2. **Adding New Fields**:
   - Add label in `.cfg` file
   - Create setter command in `.cls` file
   - Implement conditional logic if needed

## Troubleshooting

If content appears incorrectly:

1. Verify both the implementation (.cls) and label (.cfg) files
2. Check for language suffix consistency (\_english* vs \_chinese*)
3. Ensure blind review conditions are properly nested

Happy writingthesis ! 祝家人们写毕业论文快乐！

```

This README includes:
1. Clear directory structure
2. Multiple blind review configuration methods
3. Language switching explanation
4. Template extension guidelines
5. Troubleshooting tips

The markdown format makes it easy to display on GitHub/GitLab while maintaining good readability. The Chinese/English mix matches the template's bilingual nature.
```

Special Thanks to https://github.com/sci-m-wang/NEU-Thesis
