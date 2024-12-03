
# Notes

- **JavaScript or PHP code is not allowed when using WP.com.** This is because sites that live on the WP.com servers share the same files for WP functions. `functions.php` cannot be edited for this reason.
- `<script>` and `<style>` are not allowed in HTML content blocks in WP for security reasons.
- This solution was derived by using **HTML and CSS only**. When a user selects an option, hidden CSS feedback is revealed. The only drawback to this solution is that you cannot reveal both the correct and incorrect answer when the user selects an option. However, with two choices, it will be apparent to the user which answer is correct or incorrect after selecting an option.
- It is still possible to give hints and feedback.

## HTML Code

- **Templates at the bottom of the document:**
  - Choice 1 is GIF by default.
  - Choice 2 is text by default.
  - Change independently based on question by removing/commenting.
  - Radio button style is dependent on the user's browser.
  - Path to GIF is the URL of the GIF in the WP media browser.
  - Change which answer is correct by changing the `div` class to either:
    - `feedback correct`
    - `feedback incorrect`
  - Change text of feedback in between the class to show the user.
  - For multiple MCQ sections on one page, remember to:
    - Change the `id` and `label` to `mcq(n)`.
      - For example:
        - `id="mcq1-choice1"`
        - `id="mcq1-choice2"`
    - Then for the second MCQ later in the page:
        - `id="mcq2-choice1"`
        - `id="mcq2-choice2"`

## CSS Code

- **Applied globally:**
  - For `.mcq-choice`:
    - `margin-bottom` of `0px` to bring the radio buttons lower.
  - For `.mcq-choice input[type="radio"]`:
    - Webkit radio buttons are disabled for custom buttons.
    - Improved visibility.
    - Positioning radio button with `checked::after` (Black circle) can be finicky.
    - For each 5 pixels increased in the size, the position should subtract 2 pixels depending on future GIF dimensions.
    - Use this calculator to find the correct pixel length for the border.
    - **TODO:** This should be made automatic.
  - GIF border changes to green/red if correct/incorrect.
    - This makes it more important to change the label for MCQ.
