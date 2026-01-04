---
title: مفاهيم Bloc
description: نظرة عامة على المفاهيم الأساسية لحزمة bloc:.
sidebar:
  order: 1
---

import CountStreamSnippet from '~/components/concepts/bloc/CountStreamSnippet.astro';
import SumStreamSnippet from '~/components/concepts/bloc/SumStreamSnippet.astro';
import StreamsMainSnippet from '~/components/concepts/bloc/StreamsMainSnippet.astro';
import CounterCubitSnippet from '~/components/concepts/bloc/CounterCubitSnippet.astro';
import CounterCubitInitialStateSnippet from '~/components/concepts/bloc/CounterCubitInitialStateSnippet.astro';
import CounterCubitInstantiationSnippet from '~/components/concepts/bloc/CounterCubitInstantiationSnippet.astro';
import CounterCubitIncrementSnippet from '~/components/concepts/bloc/CounterCubitIncrementSnippet.astro';
import CounterCubitBasicUsageSnippet from '~/components/concepts/bloc/CounterCubitBasicUsageSnippet.astro';
import CounterCubitStreamUsageSnippet from '~/components/concepts/bloc/CounterCubitStreamUsageSnippet.astro';
import CounterCubitOnChangeSnippet from '~/components/concepts/bloc/CounterCubitOnChangeSnippet.astro';
import CounterCubitOnChangeUsageSnippet from '~/components/concepts/bloc/CounterCubitOnChangeUsageSnippet.astro';
import CounterCubitOnChangeOutputSnippet from '~/components/concepts/bloc/CounterCubitOnChangeOutputSnippet.astro';
import SimpleBlocObserverOnChangeSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnChangeSnippet.astro';
import SimpleBlocObserverOnChangeUsageSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnChangeUsageSnippet.astro';
import SimpleBlocObserverOnChangeOutputSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnChangeOutputSnippet.astro';
import CounterCubitOnErrorSnippet from '~/components/concepts/bloc/CounterCubitOnErrorSnippet.astro';
import SimpleBlocObserverOnErrorSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnErrorSnippet.astro';
import CounterCubitOnErrorOutputSnippet from '~/components/concepts/bloc/CounterCubitOnErrorOutputSnippet.astro';
import CounterBlocSnippet from '~/components/concepts/bloc/CounterBlocSnippet.astro';
import CounterBlocEventHandlerSnippet from '~/components/concepts/bloc/CounterBlocEventHandlerSnippet.astro';
import CounterBlocIncrementSnippet from '~/components/concepts/bloc/CounterBlocIncrementSnippet.astro';
import CounterBlocUsageSnippet from '~/components/concepts/bloc/CounterBlocUsageSnippet.astro';
import CounterBlocStreamUsageSnippet from '~/components/concepts/bloc/CounterBlocStreamUsageSnippet.astro';
import CounterBlocOnChangeSnippet from '~/components/concepts/bloc/CounterBlocOnChangeSnippet.astro';
import CounterBlocOnChangeUsageSnippet from '~/components/concepts/bloc/CounterBlocOnChangeUsageSnippet.astro';
import CounterBlocOnChangeOutputSnippet from '~/components/concepts/bloc/CounterBlocOnChangeOutputSnippet.astro';
import CounterBlocOnTransitionSnippet from '~/components/concepts/bloc/CounterBlocOnTransitionSnippet.astro';
import CounterBlocOnTransitionOutputSnippet from '~/components/concepts/bloc/CounterBlocOnTransitionOutputSnippet.astro';
import SimpleBlocObserverOnTransitionSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnTransitionSnippet.astro';
import SimpleBlocObserverOnTransitionUsageSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnTransitionUsageSnippet.astro';
import SimpleBlocObserverOnTransitionOutputSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnTransitionOutputSnippet.astro';
import CounterBlocOnEventSnippet from '~/components/concepts/bloc/CounterBlocOnEventSnippet.astro';
import SimpleBlocObserverOnEventSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnEventSnippet.astro';
import SimpleBlocObserverOnEventOutputSnippet from '~/components/concepts/bloc/SimpleBlocObserverOnEventOutputSnippet.astro';
import CounterBlocOnErrorSnippet from '~/components/concepts/bloc/CounterBlocOnErrorSnippet.astro';
import CounterBlocOnErrorOutputSnippet from '~/components/concepts/bloc/CounterBlocOnErrorOutputSnippet.astro';
import CounterCubitFullSnippet from '~/components/concepts/bloc/CounterCubitFullSnippet.astro';
import CounterBlocFullSnippet from '~/components/concepts/bloc/CounterBlocFullSnippet.astro';
import AuthenticationStateSnippet from '~/components/concepts/bloc/AuthenticationStateSnippet.astro';
import AuthenticationTransitionSnippet from '~/components/concepts/bloc/AuthenticationTransitionSnippet.astro';
import AuthenticationChangeSnippet from '~/components/concepts/bloc/AuthenticationChangeSnippet.astro';
import DebounceEventTransformerSnippet from '~/components/concepts/bloc/DebounceEventTransformerSnippet.astro';

:::note

يرجى التأكد من قراءة الأقسام التالية بعناية قبل البدء بالعمل مع حزمة
[`package:bloc`](https://pub.dev/packages/bloc).

:::

هناك العديد من المفاهيم الأساسية التي تعتبر **حاسمة** لفهم كيفية استخدام حزمة bloc.

في الأقسام القادمة، سنناقش كل مفهوم منها بالتفصيل، وسنستعرض كيفية تطبيقها على تطبيق عداد (counter app).

## Streams (التدفقات)

:::note

اطلع على [وثائق Dart الرسمية](https://dart.dev/tutorials/language/streams) للحصول على مزيد من المعلومات حول `Streams`.

:::

الـ `Stream` هو تسلسل من البيانات غير المتزامنة (asynchronous data).

لاستخدام مكتبة bloc، من الضروري أن يكون لديك فهم أساسي لـ `Streams` وكيفية عملها.

إذا لم تكن على دراية بـ `Streams`، فما عليك سوى التفكير في أنبوب يتدفق فيه الماء. الأنبوب هو الـ `Stream` والماء هو البيانات غير المتزامنة.

يمكننا إنشاء `Stream` في Dart بكتابة دالة `async*` (مولد غير متزامن).

<CountStreamSnippet />

من خلال وسم الدالة بـ `async*`، نتمكن من استخدام الكلمة المفتاحية `yield` وإرجاع `Stream` من البيانات. في المثال أعلاه، نقوم بإرجاع `Stream` من الأعداد الصحيحة حتى المعامل `max` من النوع `integer`.

في كل مرة نستخدم فيها `yield` في دالة `async*`، فإننا ندفع قطعة البيانات تلك عبر الـ `Stream`.

يمكننا استهلاك الـ `Stream` أعلاه بعدة طرق. إذا أردنا كتابة دالة لإرجاع مجموع `Stream` من الأعداد الصحيحة، فقد تبدو كالتالي:

<SumStreamSnippet />

من خلال وسم الدالة أعلاه بـ `async`، نتمكن من استخدام الكلمة المفتاحية `await` وإرجاع `Future` من الأعداد الصحيحة. في هذا المثال، ننتظر كل قيمة في الـ `Stream` ونعيد مجموع جميع الأعداد الصحيحة في الـ `Stream`.

يمكننا تجميع كل ذلك معًا على النحو التالي:

<StreamsMainSnippet />

الآن بعد أن أصبح لدينا فهم أساسي لكيفية عمل `Streams` في Dart، أصبحنا جاهزين للتعرف على المكون الأساسي لحزمة bloc: وهو الـ `Cubit`.

## Cubit

الـ `Cubit` هو فئة (class) ترث من `BlocBase` ويمكن توسيعها لإدارة أي نوع من الـ `state` (الحالة).

![Cubit Architecture](~/assets/concepts/cubit_architecture_full.png)

يمكن لـ `Cubit` أن يكشف عن دوال يمكن استدعاؤها لتشغيل تغييرات الـ `state`.

الـ `States` هي مخرجات الـ `Cubit` وتمثل جزءًا من حالة تطبيقك. يمكن إخطار مكونات واجهة المستخدم (UI) بالـ `states` وإعادة رسم أجزاء منها بناءً على الـ `state` الحالية.

:::note

لمزيد من المعلومات حول أصول `Cubit`، اطلع على [المشكلة التالية](https://github.com/felangel/cubit/issues/69).

:::

### إنشاء Cubit

يمكننا إنشاء `CounterCubit` كالتالي:

<CounterCubitSnippet />

عند إنشاء `Cubit`، نحتاج إلى تحديد نوع الـ `state` الذي سيديره الـ `Cubit`. في حالة `CounterCubit` أعلاه، يمكن تمثيل الـ `state` عبر `int`، ولكن في الحالات الأكثر تعقيدًا قد يكون من الضروري استخدام `class` بدلاً من نوع أولي (primitive type).

الشيء الثاني الذي نحتاج إلى القيام به عند إنشاء `Cubit` هو تحديد الـ `initial state` (الحالة الأولية). يمكننا القيام بذلك عن طريق استدعاء `super` بقيمة الـ `initial state`. في المقتطف أعلاه، نقوم بتعيين الـ `initial state` إلى `0` داخليًا، ولكن يمكننا أيضًا جعل الـ `Cubit` أكثر مرونة من خلال قبول قيمة خارجية:

<CounterCubitInitialStateSnippet />

هذا سيسمح لنا بإنشاء نسخ من `CounterCubit` بـ `initial states` مختلفة مثل:

<CounterCubitInstantiationSnippet />

### تغييرات حالة Cubit (Cubit State Changes)

كل `Cubit` لديه القدرة على إخراج `state` جديدة عبر `emit`.

<CounterCubitIncrementSnippet />

في المقتطف أعلاه، يكشف `CounterCubit` عن دالة عامة تسمى `increment` يمكن استدعاؤها خارجيًا لإخطار `CounterCubit` بزيادة الـ `state` الخاصة به. عند استدعاء `increment`، يمكننا الوصول إلى الـ `state` الحالية للـ `Cubit` عبر الـ `getter` المسمى `state` ونقوم بعمل `emit` لـ `state` جديدة عن طريق إضافة 1 إلى الـ `state` الحالية.

:::caution

دالة `emit` محمية (`protected`)، مما يعني أنه يجب استخدامها فقط داخل `Cubit`.

:::

### استخدام Cubit

يمكننا الآن أخذ `CounterCubit` الذي قمنا بتنفيذه ووضعه موضع الاستخدام!

#### الاستخدام الأساسي (Basic Usage)

<CounterCubitBasicUsageSnippet />

في المقتطف أعلاه، نبدأ بإنشاء نسخة من `CounterCubit`. ثم نطبع الـ `state` الحالية للـ `Cubit` وهي الـ `initial state` (لأنه لم يتم عمل `emit` لأي `states` جديدة بعد). بعد ذلك، نستدعي دالة `increment` لتشغيل تغيير في الـ `state`. أخيرًا، نطبع الـ `state` للـ `Cubit` مرة أخرى والتي انتقلت من `0` إلى `1`، ونستدعي `close` على الـ `Cubit` لإغلاق الـ `internal state stream`.

#### استخدام الـ Stream (Stream Usage)

يكشف الـ `Cubit` عن `Stream` يسمح لنا بتلقي تحديثات الـ `state` في الوقت الفعلي:

<CounterCubitStreamUsageSnippet />

في المقتطف أعلاه، نقوم بالاشتراك في `CounterCubit` ونستدعي `print` عند كل تغيير في الـ `state`. ثم نستدعي دالة `increment` التي ستقوم بعمل `emit` لـ `state` جديدة. أخيرًا، نستدعي `cancel` على الـ `subscription` عندما لا نعد بحاجة إلى تلقي التحديثات ونغلق الـ `Cubit`.

:::note

تمت إضافة `await Future.delayed(Duration.zero)` لهذا المثال لتجنب إلغاء الـ `subscription` على الفور.

:::

:::caution

سيتم استقبال تغييرات الـ `state` اللاحقة فقط عند استدعاء `listen` على `Cubit`.

:::

### مراقبة Cubit (Observing a Cubit)

عندما يقوم `Cubit` بعمل `emit` لـ `state` جديدة، يحدث `Change` (تغيير). يمكننا مراقبة جميع التغييرات لـ `Cubit` معين عن طريق تجاوز دالة `onChange`.

<CounterCubitOnChangeSnippet />

يمكننا بعد ذلك التفاعل مع الـ `Cubit` ومراقبة جميع التغييرات التي يتم إخراجها إلى الـ `console`.

<CounterCubitOnChangeUsageSnippet />

سيقوم المثال أعلاه بإخراج:

<CounterCubitOnChangeOutputSnippet />

:::note

يحدث الـ `Change` قبل تحديث الـ `state` الخاصة بالـ `Cubit` مباشرة. يتكون الـ `Change` من الـ `currentState` (الحالة الحالية) والـ `nextState` (الحالة التالية).

:::

#### BlocObserver

إحدى الميزات الإضافية لاستخدام مكتبة bloc هي أنه يمكننا الوصول إلى جميع الـ `Changes` في مكان واحد. على الرغم من أن لدينا `Cubit` واحدًا فقط في هذا التطبيق، فمن الشائع جدًا في التطبيقات الأكبر أن يكون هناك العديد من الـ `Cubits` التي تدير أجزاء مختلفة من الـ `state` الخاصة بالتطبيق.

يمكننا إنشاء `SimpleBlocObserver` عن طريق توسيع `BlocObserver` وتجاوز دالة `onChange`:

<SimpleBlocObserverOnChangeSnippet />

يمكننا بعد ذلك استخدام `BlocObserver` عن طريق تعيينه في `Bloc.observer`:

<SimpleBlocObserverOnChangeUsageSnippet />

سيقوم المثال أعلاه بإخراج:

<SimpleBlocObserverOnChangeOutputSnippet />

#### معالجة الأخطاء (Error Handling)

في بعض الأحيان، قد تحدث أخطاء داخل `Cubit`. يمكننا مراقبة جميع الأخطاء لـ `Cubit` معين عن طريق تجاوز دالة `onError`.

<CounterCubitOnErrorSnippet />

يمكننا بعد ذلك التفاعل مع الـ `Cubit` ومراقبة جميع الأخطاء التي يتم إخراجها إلى الـ `console`.

:::note

سيتم استدعاء دالة `onError` محليًا أولاً، يتبعها دالة `onError` العامة في `BlocObserver`.

:::

<SimpleBlocObserverOnErrorSnippet />

يمكننا بعد ذلك استخدام `BlocObserver` عن طريق تعيينه في `Bloc.observer`:

<CounterCubitOnErrorOutputSnippet />

## Bloc

الـ `Bloc` هو فئة ترث من `BlocBase` ويمكن توسيعها لإدارة أي نوع من الـ `state` استجابةً لـ `events` (الأحداث).

![Bloc Architecture](~/assets/concepts/bloc_architecture_full.png)

الـ `Bloc` هو نسخة أكثر تعقيدًا من الـ `Cubit` الذي يعتمد على الـ `events` بدلاً من الدوال لتشغيل تغييرات الـ `state`.

الـ `Events` هي مدخلات الـ `Bloc` وعادة ما تكون فئات (classes) تمثل نية المستخدم.

الـ `States` هي مخرجات الـ `Bloc` وتمثل جزءًا من حالة تطبيقك.

### إنشاء Bloc

يمكننا إنشاء `CounterBloc` كالتالي:

<CounterBlocSnippet />

عند إنشاء `Bloc`، نحتاج إلى تحديد نوع الـ `Events` التي سيديرها الـ `Bloc` ونوع الـ `state` التي سيديرها. في حالة `CounterBloc` أعلاه، الـ `Events` هي `CounterEvent` والـ `state` هي `int`.

الشيء الثاني الذي نحتاج إلى القيام به عند إنشاء `Bloc` هو تحديد الـ `initial state`. يمكننا القيام بذلك عن طريق استدعاء `super` بقيمة الـ `initial state`. في المقتطف أعلاه، نقوم بتعيين الـ `initial state` إلى `0`.

الشيء الثالث الذي نحتاج إلى القيام به هو تسجيل `event handlers` (معالجات الأحداث) لربط الـ `Events` الواردة بـ `states` جديدة.

<CounterBlocEventHandlerSnippet />

في المقتطف أعلاه، نقوم بتسجيل `event handler` لـ `CounterIncrementPressed` `Event`. في كل مرة يتم فيها إضافة `CounterIncrementPressed` `Event` إلى الـ `Bloc`، سيتم استدعاء الـ `handler` الذي يتلقى الـ `Event` و `Emitter`.

يمكننا بعد ذلك استخدام الـ `Emitter` لـ `emit` `states` جديدة استجابةً لـ `Events` الواردة.

<CounterBlocIncrementSnippet />

في المقتطف أعلاه، نستخدم الـ `Emitter` لـ `emit` `state` جديدة عن طريق إضافة 1 إلى الـ `state` الحالية.

:::caution

دالة `emit` محمية، مما يعني أنه يجب استخدامها فقط داخل `Bloc` أو `Cubit`.

:::

### استخدام Bloc

يمكننا الآن أخذ `CounterBloc` الذي قمنا بتنفيذه ووضعه موضع الاستخدام!

#### الاستخدام الأساسي (Basic Usage)

<CounterBlocUsageSnippet />

في المقتطف أعلاه، نبدأ بإنشاء نسخة من `CounterBloc`. ثم نطبع الـ `state` الحالية للـ `Bloc` وهي الـ `initial state`. بعد ذلك، نستدعي دالة `add` لإضافة `CounterIncrementPressed` `Event` لتشغيل تغيير في الـ `state`. أخيرًا، نطبع الـ `state` للـ `Bloc` مرة أخرى والتي انتقلت من `0` إلى `1`، ونستدعي `close` على الـ `Bloc` لإغلاق الـ `internal state stream`.

#### استخدام الـ Stream (Stream Usage)

يكشف الـ `Bloc` عن `Stream` يسمح لنا بتلقي تحديثات الـ `state` في الوقت الفعلي:

<CounterBlocStreamUsageSnippet />

في المقتطف أعلاه، نقوم بالاشتراك في `CounterBloc` ونستدعي `print` عند كل تغيير في الـ `state`. ثم نستدعي دالة `add` التي ستقوم بعمل `emit` لـ `state` جديدة. أخيرًا، نستدعي `cancel` على الـ `subscription` عندما لا نعد بحاجة إلى تلقي التحديثات ونغلق الـ `Bloc`.

:::note

`await Future.delayed(Duration.zero)` مضافة لهذا المثال لتجنب إلغاء الـ `subscription` على الفور.

:::

:::caution

سيتم استقبال تغييرات الـ `state` اللاحقة فقط عند استدعاء `listen` على `Bloc`.

:::

### مراقبة Bloc (Observing a Bloc)

عندما يقوم `Bloc` بعمل `emit` لـ `state` جديدة، يحدث `Change`. يمكننا مراقبة جميع التغييرات لـ `Bloc` معين عن طريق تجاوز دالة `onChange`.

<CounterBlocOnChangeSnippet />

يمكننا بعد ذلك التفاعل مع الـ `Bloc` ومراقبة جميع التغييرات التي يتم إخراجها إلى الـ `console`.

<CounterBlocOnChangeUsageSnippet />

سيقوم المثال أعلاه بإخراج:

<CounterBlocOnChangeOutputSnippet />

:::note

الـ `Change` يحدث قبل تحديث الـ `state` الخاصة بالـ `Bloc` مباشرة. يتكون الـ `Change` من الـ `currentState` والـ `nextState`.

:::

#### Transitions (الانتقالات)

عندما يقوم `Bloc` بمعالجة `Event`، يحدث `Transition` (انتقال). يمكننا مراقبة جميع الـ `Transitions` لـ `Bloc` معين عن طريق تجاوز دالة `onTransition`.

<CounterBlocOnTransitionSnippet />

يمكننا بعد ذلك التفاعل مع الـ `Bloc` ومراقبة جميع الـ `Transitions` التي يتم إخراجها إلى الـ `console`.

<CounterBlocOnChangeUsageSnippet />

سيقوم المثال أعلاه بإخراج:

<CounterBlocOnTransitionOutputSnippet />

:::note

الـ `Transition` يحدث بعد معالجة الـ `Event` وقبل تحديث الـ `state` الخاصة بالـ `Bloc`. يتكون الـ `Transition` من الـ `Event` والـ `currentState` والـ `nextState`.

:::

#### BlocObserver

يمكننا الوصول إلى جميع الـ `Transitions` في مكان واحد عن طريق تجاوز دالة `onTransition` في `BlocObserver`.

<SimpleBlocObserverOnTransitionSnippet />

يمكننا بعد ذلك استخدام `BlocObserver` عن طريق تعيينه في `Bloc.observer`:

<SimpleBlocObserverOnTransitionUsageSnippet />

سيقوم المثال أعلاه بإخراج:

<SimpleBlocObserverOnTransitionOutputSnippet />

#### مراقبة الأحداث (Observing Events)

يمكننا مراقبة جميع الـ `Events` التي تتم إضافتها إلى `Bloc` معين عن طريق تجاوز دالة `onEvent`.

<CounterBlocOnEventSnippet />

يمكننا بعد ذلك التفاعل مع الـ `Bloc` ومراقبة جميع الـ `Events` التي يتم إخراجها إلى الـ `console`.

<CounterBlocOnChangeUsageSnippet />

يمكننا الوصول إلى جميع الـ `Events` في مكان واحد عن طريق تجاوز دالة `onEvent` في `BlocObserver`.

<SimpleBlocObserverOnEventSnippet />

يمكننا بعد ذلك استخدام `BlocObserver` عن طريق تعيينه في `Bloc.observer`:

<SimpleBlocObserverOnEventOutputSnippet />

#### معالجة الأخطاء (Error Handling)

في بعض الأحيان، قد تحدث أخطاء داخل `Bloc`. يمكننا مراقبة جميع الأخطاء لـ `Bloc` معين عن طريق تجاوز دالة `onError`.

<CounterBlocOnErrorSnippet />

يمكننا بعد ذلك التفاعل مع الـ `Bloc` ومراقبة جميع الأخطاء التي يتم إخراجها إلى الـ `console`.

<CounterBlocOnChangeUsageSnippet />

سيقوم المثال أعلاه بإخراج:

<CounterBlocOnErrorOutputSnippet />

:::note

سيتم استدعاء دالة `onError` المحلية أولاً، يتبعها دالة `onError` العامة في `BlocObserver`.

:::

:::note

تعمل دالتا `onError` و `onChange` بنفس الطريقة تمامًا لكل من نسخ `Bloc` و `Cubit`.

:::

:::caution

أي استثناءات غير معالجة تحدث داخل `EventHandler` يتم الإبلاغ عنها أيضًا إلى `onError`.

:::

## Cubit مقابل Bloc

الآن بعد أن قمنا بتغطية أساسيات فئتي `Cubit` و `Bloc`، قد تتساءل متى يجب عليك استخدام `Cubit` ومتى يجب عليك استخدام `Bloc`.

### مزايا Cubit

#### البساطة (Simplicity)

إحدى أكبر مزايا استخدام `Cubit` هي البساطة. عند إنشاء `Cubit`، نحتاج فقط إلى تحديد الـ `state` بالإضافة إلى الدوال التي نريد كشفها لتغيير الـ `state`. بالمقارنة، عند إنشاء `Bloc`، يجب علينا تحديد الـ `states` والـ `events` وتنفيذ `EventHandler`. هذا يجعل `Cubit` أسهل في الفهم ويتطلب قدرًا أقل من الكود.

الآن دعونا نلقي نظرة على تطبيقي العداد (counter) الاثنين:

##### CounterCubit

<CounterCubitFullSnippet />

##### CounterBloc

<CounterBlocFullSnippet />

تنفيذ `Cubit` أكثر إيجازًا، وبدلاً من تحديد الـ `events` بشكل منفصل، تعمل الدوال كـ `events`. بالإضافة إلى ذلك، عند استخدام `Cubit`، يمكننا ببساطة استدعاء `emit` من أي مكان لتشغيل تغيير في الـ `state`.

### مزايا Bloc

#### إمكانية التتبع (Traceability)

إحدى أكبر مزايا استخدام `Bloc` هي معرفة تسلسل تغييرات الـ `state` بالإضافة إلى ما أدى إلى تشغيل هذه التغييرات بالضبط. بالنسبة للـ `state` التي تعتبر حاسمة لوظيفة التطبيق، قد يكون من المفيد جدًا استخدام نهج يعتمد على الـ `event` بشكل أكبر لالتقاط جميع الـ `events` بالإضافة إلى تغييرات الـ `state`.

قد تكون حالة الاستخدام الشائعة هي إدارة `AuthenticationState` (حالة المصادقة). للتبسيط، لنفترض أنه يمكننا تمثيل `AuthenticationState` عبر `enum`:

<AuthenticationStateSnippet />

قد تكون هناك أسباب عديدة لتغير `state` التطبيق من `authenticated` إلى `unauthenticated`. على سبيل المثال، ربما يكون المستخدم قد نقر على زر تسجيل الخروج وطلب تسجيل الخروج من التطبيق. من ناحية أخرى، ربما تم إلغاء `access token` الخاص بالمستخدم وتم تسجيل خروجه بالقوة. عند استخدام `Bloc`، يمكننا تتبع بوضوح كيف وصلت `state` التطبيق إلى `state` معينة.

<AuthenticationTransitionSnippet />

يوفر لنا الـ `Transition` أعلاه جميع المعلومات التي نحتاجها لفهم سبب تغير الـ `state`. إذا كنا قد استخدمنا `Cubit` لإدارة `AuthenticationState`، فستبدو سجلاتنا كالتالي:

<AuthenticationChangeSnippet />

هذا يخبرنا أنه تم تسجيل خروج المستخدم ولكنه لا يوضح السبب، وهو ما قد يكون حاسمًا لتصحيح الأخطاء وفهم كيفية تغير `state` التطبيق بمرور الوقت.

#### تحويلات الأحداث المتقدمة (Advanced Event Transformations)

مجال آخر يتفوق فيه `Bloc` على `Cubit` هو عندما نحتاج إلى الاستفادة من عوامل التشغيل التفاعلية (reactive operators) مثل `buffer`، `debounceTime`، `throttle`، إلخ.

:::tip

راجع [`package:stream_transform`](https://pub.dev/packages/stream_transform) و [`package:rxdart`](https://pub.dev/packages/rxdart) لـ `stream transformers`.

:::

يحتوي `Bloc` على `event sink` يسمح لنا بالتحكم في تدفق الـ `events` الواردة وتحويله.

على سبيل المثال، إذا كنا نبني بحثًا في الوقت الفعلي، فمن المحتمل أننا نريد تطبيق `debounce` على الطلبات إلى الواجهة الخلفية لتجنب الوصول إلى حد المعدل (rate-limited) وكذلك لتقليل التكلفة/التحميل على الواجهة الخلفية.

باستخدام `Bloc`، يمكننا توفير `EventTransformer` مخصص لتغيير طريقة معالجة الـ `Events` الواردة بواسطة الـ `Bloc`.

<DebounceEventTransformerSnippet />

باستخدام الكود أعلاه، يمكننا بسهولة تطبيق `debounce` على الـ `Events` الواردة بقليل جدًا من الكود الإضافي.

:::tip

اطلع على [`package:bloc_concurrency`](https://pub.dev/packages/bloc_concurrency) للحصول على مجموعة مختارة من `event transformers`.

:::

إذا لم تكن متأكدًا من أيهما تستخدم، فابدأ بـ `Cubit` ويمكنك لاحقًا إعادة هيكلته أو توسيعه إلى `Bloc` حسب الحاجة.
