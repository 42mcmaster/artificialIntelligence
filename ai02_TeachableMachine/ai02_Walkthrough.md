# Lesson 02 Walkthrough: Train Your First AI with Teachable Machine
**Artificial Intelligence — Medina County Career Center**

> No coding today. You'll train a real image-classification model in your browser and watch
> how it behaves. Work through every step and answer the checkpoints in your task sheet.

---

## Step 0 — Open Teachable Machine
1. Go to **https://teachablemachine.withgoogle.com**
2. Click **Get Started**.
3. Choose **Image Project** -> **Standard image model**.

You'll see two class boxes (**Class 1**, **Class 2**), a **Training** panel in the middle, and
a **Preview** panel on the right.

---

## Step 1 — Name your classes
You're going to teach the model to tell **two kinds of animals** apart (pick any two you like —
cats vs. dogs, horses vs. cows, etc.).

1. Click the **pencil** next to *Class 1* and rename it to your first animal.
2. Rename *Class 2* to your second animal.

> **Tip:** pick two animals that look fairly different to start. You can try look-alikes later.

---

## Step 2 — Add training images
For **each** class, add **3–5 images** of that animal:

- Easiest way: use a safe image search (or images your teacher provides), save 3–5 pictures to
  a folder, then click **Upload** on that class and drag them in.
- You can also use **Webcam** to capture images of toy or stuffed animals.

Do this for **both** classes. Each class should now show its little gallery of examples.

**Checkpoint A:** How many images did you give each class?

---

## Step 3 — Train the model
1. Click the big **Train Model** button in the middle.
2. Wait a few seconds — **keep the tab open** while it trains.
3. (Optional) Click **Advanced** to peek at settings like *epochs* and *learning rate* — you'll
   meet those words again in the neural-network lessons.

When it finishes, the **Preview** panel becomes active.

---

## Step 4 — Test with NEW images
This is the important part — test on images the model has **never seen**.

1. Find a **new** picture of one of your two animals (not one you trained on). Save it.
2. In the **Preview** panel, set **Input** to **On**, choose **File** from the dropdown, and
   upload your new image. (If it sticks, switch to **Webcam** then back to **File**.)
3. Look at the output bars: the model shows a **confidence %** for each class.

**Checkpoint B:** What did it predict, and with what confidence? Was it correct?

Try **2–3 more** new images and record each result.

---

## Step 5 — Add more data and retrain
1. Go back and add **2–3 more** training images to **each** class (different from your test
   images).
2. Click **Train Model** again.
3. Re-test your same test images from Step 4.

**Checkpoint C:** Did the confidence or accuracy change after adding more training data?

---

## Step 6 — Try to break it (optional but fun)
- Test an image that's **between** your two classes, or a **look-alike** animal. What happens?
- Add a **third class** and retrain. Does it get harder?
- Start a fresh project and train it on **colors** or **hand gestures** with your webcam.

---

## What just happened?
You did **supervised learning**:
- Your labeled images were the **training data**.
- **Train Model** found patterns separating the classes.
- Testing on new images measured how well it **generalizes**.
- More (and more varied) training data usually means better predictions.

Every model this year works this way under the hood. Next, you'll do it **in Python** — and
see the parts Teachable Machine hides. Now finish the **Task sheet**.
