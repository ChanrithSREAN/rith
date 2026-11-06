# Step-by-Step Guide to Using AI Effectively

A practical guide for using AI as a study and coding assistant. AI can help you understand ideas, explore options, and find mistakes, but it can also produce confident, incorrect answers. Stay involved and verify important results.

## Step 1: Decide what you need

Before opening an AI tool, write down your goal. Are you trying to:

- Understand a concept?
- Get unstuck on an exercise?
- Review code or an error message?
- Plan a project?
- Improve writing or prepare for an exam?

A specific goal makes it easier to get a useful answer.

## Step 2: Try the problem yourself first

Spend a few minutes examining the question, writing down what you know, or trying a solution. Note where you got stuck. This gives the AI useful context and helps you learn instead of simply copying an answer.

For coding, collect:

- What you expected to happen.
- What actually happened.
- The relevant code and error message.
- What you already tried.

## Step 3: Give the AI useful context

Explain your situation clearly. Include your experience level, the goal, any requirements, and what you have attempted. Remove information that is private or unrelated.

Instead of:

```text
Help me with Java.
```

Try:

```text
I am a beginner learning Java methods. I understand variables and if-statements,
but I do not understand how a method returns a value. Explain it with a small
example, then give me one practice question without its answer.
```

## Step 4: Ask for the kind of help you want

Tell the AI how to respond. For example, ask it to:

- Explain an idea in simple language.
- Give hints one at a time.
- Show a small example and explain each part.
- Compare two approaches and their trade-offs.
- Review your attempt without rewriting it.
- Ask you questions to check your understanding.

If the first answer is too long or advanced, say so and ask for a simpler explanation.

## Step 5: Use a prompt structure

A useful prompt often includes these parts:

```text
Role: Act as a patient programming tutor.
Goal: Help me understand [topic or task].
My level: [beginner/intermediate] and what I already know: [details].
Context: [instructions, code, error, or work so far].
Request: [the specific help you want].
Format: [steps, short explanation, hints, example, or questions].
Limits: [things to avoid, such as giving the full solution immediately].
```

You do not need every part for every question. Include the details that matter.

## Step 6: Work in small rounds

Do not try to solve a large assignment in one prompt. Break it into stages:

1. Ask for an explanation or plan.
2. Check that you understand the plan.
3. Work on one part yourself.
4. Ask for feedback on that part.
5. Test or verify the result.
6. Summarize what you learned in your own words.

If the task changes, provide the new information instead of assuming the AI remembers or inferred it correctly.

## Step 7: For coding, ask for help without giving up the learning

A useful coding workflow is:

1. Describe the expected and actual behavior.
2. Share the smallest relevant code sample and exact error text.
3. Ask the AI to explain the likely cause before suggesting a change.
4. Ask for a hint or a minimal fix that fits your current code.
5. Read the proposed change and make sure you can explain it.
6. Run the program and relevant tests yourself.
7. Try edge cases, such as empty input or unexpected values.

Example prompt:

```text
I am learning Java and this method should return the largest number in an array,
but it returns the first number instead. Here is my method and a sample input.
Please explain the likely logic error and give me a hint first. Do not rewrite the
whole program. Also suggest two test cases I can run.
```

Do not paste secrets, passwords, API keys, private keys, or private user data into an AI tool. Share only the code and context needed to diagnose the issue.

## Step 8: Check the answer

Treat AI output as a suggestion, not proof. Verify it by:

- Comparing factual claims with course materials or reliable documentation.
- Running code and tests in your own environment.
- Checking assumptions, versions, and requirements.
- Asking the AI what assumptions it made and what could be wrong.
- Seeking another source for important or unfamiliar claims.

A confident tone does not guarantee correctness. Be especially careful with security, health, legal, financial, and other high-impact advice.

## Step 9: Improve the conversation

If the answer misses the mark, be specific about what to change:

```text
That explanation assumes I know recursion. Please explain the idea using a loop
first, then compare it with recursion.
```

```text
Your suggestion does not meet the requirement that the program use an array.
Please revise the approach while keeping that requirement.
```

Share corrections and constraints as soon as you notice them. You can also ask the AI to list uncertainties rather than guess.

## Step 10: Finish by learning and taking responsibility

Before using an answer in your work, ask yourself:

- Can I explain the result without reading the AI response?
- Did I test it or verify its claims?
- Does it follow the assignment and project requirements?
- Am I allowed to use AI for this task, and do I need to disclose that use?

Follow your instructor's or organization's AI rules. Do not submit generated work as your own if that is prohibited. Use AI to strengthen your understanding, and be transparent when disclosure is required.

## Ready-to-use prompts

### Learn a concept

```text
Teach me [topic] as a beginner. Start with a simple explanation and one small
example. Then ask me two questions to check my understanding. Do not show the
answers until I try.
```

### Get a hint

```text
I am working on [problem]. My attempt is [your attempt]. I am stuck at [specific
point]. Give me one hint at a time, starting with a small hint. Do not provide the
full solution unless I ask.
```

### Review code

```text
Review this code for correctness and readability. First identify potential bugs
and explain why they matter. Do not rewrite the whole program. Suggest focused
changes and test cases. [Paste relevant code]
```

### Understand an error

```text
Explain this error in beginner-friendly language. What does it usually mean, what
part of my code may cause it, and what should I inspect first? Do not assume the
cause without explaining your reasoning. [Paste error and relevant code]
```

### Prepare for an exam

```text
Quiz me on [topic] at [beginner/intermediate] level, one question at a time. Wait
for my answer, explain any mistake, and keep track of the areas I should review.
```

### Plan a project

```text
Help me break [project idea] into small milestones. Ask about missing requirements
first. For each milestone, describe the goal and a way I can test it. Do not
write the entire project for me.
```

## Quick checklist

Before sending a prompt:

- [ ] Have I stated the goal clearly?
- [ ] Have I included relevant context and what I tried?
- [ ] Have I said what kind of help or format I want?
- [ ] Have I removed private or sensitive information?

Before relying on an answer:

- [ ] Have I checked it against requirements and reliable sources?
- [ ] Have I run the code or tested the recommendation where possible?
- [ ] Can I explain the result in my own words?
- [ ] Have I followed the rules for this task?
